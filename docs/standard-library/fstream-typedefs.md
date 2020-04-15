---
title: '&lt;fstream&gt; typedefs'
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
ms.openlocfilehash: 57e481c131a6e4a1111b1ed88217b891d6fc96a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317195"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

||||
|-|-|-|
|[filebuf (właśc.](#filebuf)|[fstream (fstream)](#fstream)|[Ifstream](#ifstream)|
|[Ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>filebuf (właśc.

Typ `basic_filebuf` wyspecjalizowany w parametrach szablonu **znaku.**

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_filebuf,](../standard-library/basic-filebuf-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="fstream"></a><a name="fstream"></a>fstream (fstream)

Typ `basic_fstream` wyspecjalizowany w parametrach szablonu **znaku.**

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_fstream,](../standard-library/basic-fstream-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="ifstream"></a><a name="ifstream"></a>Ifstream

Definiuje strumień, który ma być używany do odczytywania danych znaków jedno bajtowych szeregowo z pliku. `ifstream`jest typedef, który specjalizuje `basic_ifstream` się szablon klasy dla **char**.

Istnieje również `wifstream`, typedef, `basic_ifstream` który specjalizuje się w czytania **wchar_t** znaków o podwójnej szerokości. Aby uzyskać więcej informacji, zobacz [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ifstream,](../standard-library/basic-ifstream-class.md)wyspecjalizowane dla elementów typu char z domyślnymi cechami znaków. Przykładem jest

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>Ofstream

Typ `basic_ofstream` wyspecjalizowany w parametrach szablonu **znaku.**

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ofstream,](../standard-library/basic-ofstream-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

Typ `basic_fstream` wyspecjalizowany w **parametrach szablonu wchar_t.**

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_fstream,](../standard-library/basic-fstream-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="wifstream"></a><a name="wifstream"></a>wifstream

Typ `basic_ifstream` wyspecjalizowany w **parametrach szablonu wchar_t.**

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ifstream,](../standard-library/basic-ifstream-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="wofstream"></a><a name="wofstream"></a>wofstream

Typ `basic_ofstream` wyspecjalizowany w **parametrach szablonu wchar_t.**

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ofstream,](../standard-library/basic-ofstream-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf

Typ `basic_filebuf` wyspecjalizowany w **parametrach szablonu wchar_t.**

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_filebuf,](../standard-library/basic-filebuf-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="see-also"></a>Zobacz też

[\<>fstream](../standard-library/fstream.md)
