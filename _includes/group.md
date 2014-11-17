### <a name="group">group</a>

Group resource type.

#### exist

In order to test a group exists, you should use **exist** matcher.

```ruby
describe group('wheel') do
  it { should exist }
end
```

```ruby
describe group('wheel') do
  it "exists" do
    expect(subject).to exist
  end
end
```

#### have\_gid

In order to test a group have a given gid, you should use **have\_gid** matcher.

```ruby
describe group('root') do
  it { should have_gid 0 }
end
```

```ruby
describe group('root') do
  it "has the correct gid" do
    expect(subject).to have_gid(0)
  end
end
```
