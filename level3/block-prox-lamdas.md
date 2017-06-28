#### Block

  + Tập hợp các câu lệnh thành 1 khối
  + Được đặt trong dấu {} hoặc do ... end
  + Phổ biến và dễ dùng hơn lambda và proc.

  [1,2,3].each { |x|
    puts "Number: "
    puts x }

  [1,2,3].each do |x|
    puts "Number: "
    puts x
  end

  Number:
  1
  Number:
  2
  Number:
  3
   => [1, 2, 3]


#### Proc

  + Block: thay đổi đầu vào thì cần viết lại toàn bộ code.
  Ý tưởng: Đặt tên cho block. khi nào cần thì gọi => Proc

  proc = Proc.new {|x|
    puts "Number: "
    puts x
  }             // p chính là tên của block cần sử dụng

  [1,2,3].each(&proc)
  Number:
  1
  Number:
  2
  Number:
  3
   => [1, 2, 3]

   Kí hiệu & để hiểu tham số truyền vào là 1 proc.
   Bản chất chuyển symbol thành một proc object, truyền vào như 1 block.
   Proc chính là 1 object.


  proc.call(1)  # Các câu lệnh trong đối tượng Proc sẽ được thực hiện khi gọi
  Number:
  1
  => nil

  proc.call()
  proc.call
  Number:

   => nil


#### Lambda

-
  # có 2 cách khai báo đối tượng proc
  proc = Proc.new { puts "Hello world" }
  another_proc = proc { puts "Hello world" } #<Proc:0x007fd7ba81bbb0@(pry):4>

  # khai báo lambda
  lam = lambda { puts "Hello world" } #<Proc:0x007fd7ba202b20@(pry):5 (lambda)>

– lambda kiểm tra số lượng tham số đầu vào và trả về một ArgumentError nếu số lượng truyền vào không đúng với tham số được khai báo trong method của nó; còn Proc thì không kiểm tra số lượng tham số đầu vào và mặc định tham số đó là nil

-
def proc_method
    proc = Proc.new { return 1 + 1 }
    proc.call

    return 2 + 2
  end

  def lambda_method
    lam = lambda { return 1 + 1 }
    lam.call

    return 2 + 2
  end

  // call proc and lambda method

  proc_method #=> 2
  lambda_method #=> 4
