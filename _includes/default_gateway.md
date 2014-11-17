### <a name="default_gateway">default_gateway</a>

Default gateway resource type.

In order to test a default gateway is set up correctly, you should use this syntax.

```ruby
describe default_gateway do
  its(:ipaddress) { should eq '192.168.10.1' }
  its(:interface) { should eq 'br0'          }
end
```

```ruby
describe default_gateway do
  it "has the correct ip address" do
    expect(subject.ipaddress).to eq '192.168.10.1'
  end

  it "has the correct interface" do
    expect(subject.interface).to eq 'br0'
  end
end
```
