### <a name="windows_feature">windows_feature</a>

Windows Feature resource type.

#### installed

In order to test that a windows feature has been installed, you should use **installed** matcher.

```ruby
describe windows_feature('Minesweeper') do
  it{ should be_installed }
end
```

```ruby
describe windows_feature('Minesweeper') do
  it "installed" do
    expect(subject).to be_installed
  end
end
```

You can optionally specify the method used to check the windows feature, as the same feature can have different names.

```ruby
describe windows_feature('IIS-Webserver') do
  it{ should be_installed.by("dism") }
end

describe windows_feature('Web-Webserver') do
  it{ should be_installed.by("powershell") }
end
```

```ruby
describe windows_feature('IIS-Webserver') do
  it "installed by dism" do
    expect(subject).to be_installed.by("dism")
  end
end

describe windows_feature('Web-Webserver') do
  it "installed by powershell" do
    expect(subject).to be_installed.by("powershell")
  end
end
```
