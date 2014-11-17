### <a name="zfs">zfs</a>

ZFS resource type.

#### exist

In order to test a given zfs pool exists,  you should use **exist** matcher.

```ruby
describe zfs('rpool') do
  it { should exist }
end
```

```ruby
describe zfs('rpool') do
  it "exists" do
    expect(subject).to exist
  end
end
```

#### have_property

In order to test a zfs pool has given properties,  you should use **have_property** matcher.

```ruby
describe zfs('rpool') do
  it { should have_property 'mountpoint' => '/rpool', 'compression' => 'off' }
end
```

```ruby
describe zfs('rpool') do
  it "has correct property" do
    expect(subject).to have_property('mountpoint' => '/rpool', 'compression' => 'off')
  end
end
```
