---
title: '&lt;fstream &gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 3f4104b28f5becfdbf62ede16faa81e855fcac8c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689651"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream &gt; Typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream —](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>filebuf

Typ `basic_filebuf` wyspecjalizowany w parametrach szablonu **char** .

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [basic_filebuf](../standard-library/basic-filebuf-class.md)szablonu klasy, wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="fstream"></a>fstream —

Typ `basic_fstream` wyspecjalizowany w parametrach szablonu **char** .

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [basic_fstream](../standard-library/basic-fstream-class.md)szablonu klasy, wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="ifstream"></a>ifstream

Definiuje strumień, który ma być używany do odczytywania jednobajtowego danych znakowego z pliku. `ifstream` jest elementem TypeDef, który specjalizacje szablonu klasy `basic_ifstream` dla **char**.

Jest również `wifstream`, typedef, który wyspecjalizowany `basic_ifstream` do odczytu znaków **wchar_t** podwójnej precyzji. Aby uzyskać więcej informacji, zobacz [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [basic_ifstream](../standard-library/basic-ifstream-class.md)szablonu klasy, wyspecjalizowany dla elementów typu char z domyślnymi cechami znaków. Przykładem jest

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>ofstream

Typ `basic_ofstream` wyspecjalizowany w parametrach szablonu **char** .

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [basic_ofstream](../standard-library/basic-ofstream-class.md)szablonu klasy, wyspecjalizowany dla elementów typu **char** z domyślnymi cechami znaków.

## <a name="wfstream"></a>wfstream

Typ `basic_fstream` wyspecjalizowany w parametrach szablonu **wchar_t** .

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_fstream](../standard-library/basic-fstream-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="wifstream"></a>wifstream

Typ `basic_ifstream` wyspecjalizowany w parametrach szablonu **wchar_t** .

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ifstream](../standard-library/basic-ifstream-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="wofstream"></a>wofstream

Typ `basic_ofstream` wyspecjalizowany w parametrach szablonu **wchar_t** .

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ofstream](../standard-library/basic-ofstream-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="wfilebuf"></a>wfilebuf

Typ `basic_filebuf` wyspecjalizowany w parametrach szablonu **wchar_t** .

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_filebuf](../standard-library/basic-filebuf-class.md), wyspecjalizowany dla elementów typu **wchar_t** z cechami domyślnymi znaków.

## <a name="see-also"></a>Zobacz także

[\<fstream >](../standard-library/fstream.md)
