Rails callback tips
========================

#### 1: 顺序
    1 before_validation
    2 after_validation
    3 before_save
    4 before_create ( before_update , before_destroy )
    5 around_create ( around_update , around_destroy )
    6 after_create (after_update , after_destroy )
    7 around_save
    8 after_save
    9 after_commit
------------------
