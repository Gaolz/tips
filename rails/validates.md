Rails validates tips
========================

#### 1: object vs object_id
```ruby
class Topping  < ActiveRecord::Base
    belongs_to :pancake
    validates  :pancake, presence: true
    ...

class Topping  < ActiveRecord::Base
    belongs_to :pancake
    validates  :pancake_id, presence: true
    ...
```
  * 当验证 object_id 时，只判断是否有值，超出范围的值也会通过验证。
  * 当验证 object 时，rails 会去数据库中加载该对象，找到了才会通过。

------------------
