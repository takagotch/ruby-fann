### ruby-fann
---
https://github.com/tangledpath/ruby-fann

```ruby
require 'ruby-fann'
train = RubyFann::TrainData.new(:inputs=>[[0.3, 0.4, 0.5]], [0.1, 0.2, 0.3], :desired_outputs=>[0.7], [0.8])
fann = RubyFann::Standard.new(:num_inputs=>3, :hidden_neurons=>[2, 8, 4, 3, 4], :num_outputs=>1)
fann.train_on_data(train, 1000, 10, 0.1)
outputs = fann.run([0.3, 0.2, 0.4])

train.save('verify.train')
train = RubyFann::TrainData.new(:filename=>'verify.train')
fann.train_on_data(train, 10000, 20, 0.01)

fann.save('foo.net')
saved_nn = RubyFann::Standard.new(:filename=>"foo.net")
saved_nn.run([0.3, 0.2, 0.4])

class MyFann < RubyFann::Standard
  def training_callback(args)
    puts "ARGS: #{args.inspect}"
    0
  end
end

```

```
gem 'ruby-fann'
bundle
gem install ruby-fann


```

```
```
