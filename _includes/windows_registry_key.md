### <a name="windows_registry_key">windows\_registry\_key</a>

Windows Registry Key resource type.

Matchers that reference the data type of the registry key will accept any of the following identifiers;

- :type_string
- :type_binary
- :type_dword
- :type_qword
- :type_multistring
- :type_expandstring


#### exist

In order to test that a key exists in the registry, you should use **exist** matcher.

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it { should exist }
end
```

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it "exists" do
    expect(subject).to exist
  end
end
```

#### have\_property

In order to test a registry key contains a specific property, you should use the **have\_property** matcher.

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it { should have_property('string value') }
  it { should have_property('binary value', :type_binary) }
  it { should have_property('dword value', :type_dword) }
end
```

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it "has correct string value" do
    expect(subject).to have_property('string value')
  end

  it "has correct binary value" do
    expect(subject).to have_property('binary value', :type_binary)
  end

  it "has correct dword value" do
    expect(subject).to have_property('dword value', :type_dword)
  end
end
```

#### have_value

In order to test that a registry key property has the correct value, you should use the **have\_value** matcher.

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it { should have_value('test default data') }
end
```

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it "has the correct value" do
    expect(subject).to have_value('test default data')
  end
end
```

#### have\_property\_value

In order to test that a registry key property has the correct value and data type, you should use the **have\_property\_value** matcher.

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it { should have_property_value('multistring value', :type_multistring, "test\nmulti\nstring\ndata") }
  it { should have_property_value('qword value', :type_qword, 'adff32') }
  it { should have_property_value('binary value', :type_binary, 'dfa0f066') }
end
```

```ruby
describe windows_registry_key('HKEY_USERS\S-1-5-21\Test MyKey') do
  it "correct 'multistring value'" do
    expect(subject).to have_property_value('multistring value', :type_multistring, "test\nmulti\nstring\ndata")
  end

  it "correct 'qword value'" do
    expect(subject).to have_property_value('qword value', :type_qword, 'adff32')
  end

  it "correct 'binary value" do
    expect(subject).to have_property_value('binary value', :type_binary, 'dfa0f066')
  end
end
```


