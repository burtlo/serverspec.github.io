### <a name="iptables">iptables</a>

Iptables resource type.

#### have\_rule

In order to test iptables has a given rule, you should use **have\_rule** matcher.

```ruby
describe iptables do
  it { should have_rule('-P INPUT ACCEPT') }
end
```

```ruby
describe iptables do
  it "has the correct rule" do
    expect(subject).to have_rule('-P INPUT ACCEPT')
  end
end
```

You can give a table name and a chain name like this.

```ruby
describe iptables do
  it { should have_rule('-P INPUT ACCEPT').with_table('mangle').with_chain('INPUT') }
end
```

```ruby
describe iptables do
  it "has the correct rule" do
    expect(subject).to have_rule('-P INPUT ACCEPT').with_table('mangle').with_chain('INPUT')
  end
end
```
