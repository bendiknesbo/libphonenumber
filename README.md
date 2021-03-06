libphonenumber
==============

[![PkgGoDev](https://pkg.go.dev/badge/github.com/bendiknesbo/libphonenumber)](https://pkg.go.dev/github.com/bendiknesbo/libphonenumber)
[![GitHubActions](https://github.com/bendiknesbo/libphonenumber/workflows/Test/badge.svg)](https://github.com/bendiknesbo/libphonenumber/actions?query=workflow%3ATest)


golang port of Google's libphonenumber

This is a port of https://github.com/ttacon/libphonenumber

Forked to add go module-version.

Status
======

This library is fully stable and is used in production by several companies.

Examples
========

Super simple to use.

### To get a phone number

```go
num, err := libphonenumber.Parse("6502530000", "US")
```

### To format a number

```go
// num is a *libphonenumber.PhoneNumber
formattedNum := libphonenumber.Format(num, libphonenumber.NATIONAL)
```

### To get the area code of a number
```go
// Parse the number.
num, err := libphonenumber.Parse("1234567890", "US")
if err != nil {
        // Handle error appropriately.
}

// Get the cleaned number and the length of the area code.
natSigNumber := libphonenumber.GetNationalSignificantNumber(num)
geoCodeLength := libphonenumber.GetLengthOfGeographicalAreaCode(num)

// Extract the area code.
areaCode := ""
if geoCodeLength > 0 {
        areaCode = natSigNumber[0:geoCodeLength]
}
fmt.Println(areaCode)
```