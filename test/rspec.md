Rspec tips
========================

#### 1: [Test accurate time](http://stackoverflow.com/questions/20403063/trouble-comparing-time-with-rspec)
  * using the `be_within`
  > `expect(@article.updated_at).to be_within(1.second).of Time.now`
-----
