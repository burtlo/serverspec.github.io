### <a name="interface">interface</a>

Network interface resource type.

In order to test a network interface is set up correctly, you should use this syntax.

```ruby
describe interface('eth0') do
  its(:speed) { should eq 1000 }
end
```

```ruby
describe interface('eth0') do
  it "has correct speed" do
    expect(subject.speed).to eq(1000)
  end
end
```

#### have\_ipv4\_address

In order to test a interface has a ip address, you should use **have\_ipv4\_address** matcher.

```ruby
describe interface('eth0') do
  it { should have_ipv4_address("192.168.10.10") }
  it { should have_ipv4_address("192.168.10.10/24") }
end
```

```ruby
describe interface('eth0') do
  it "has the correct ipv4 adddress" do
    expect(subject).to have_ipv4_address("192.168.10.10")
  end
  it "has the correct ipv4 adddress" do
    expect(subject).to have_ipv4_address("192.168.10.10/24")
  end
end
```
