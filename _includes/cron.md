### <a name="cron">cron</a>

Cron resource type.

#### have\_entry

In order to test cron have a given entry exists, you should use **have_entry** matcher.

```ruby
describe cron do
  it { should have_entry '* * * * * /usr/local/bin/foo' }
end
```

```ruby
describe cron do
  it "has the correct entry" do
    expect(subject).to have_entry('* * * * * /usr/local/bin/foo')
  end
end
```

You can test a given user has the cron entry like this.

```ruby
describe cron do
  it { should have_entry('* * * * * /usr/local/bin/foo').with_user('mizzy') }
end
```

```ruby
describe cron do
  it "has the correct entry with user" do
    expect(subject).to have_entry('* * * * * /usr/local/bin/foo').with_user('mizzy')
  end
end
```
