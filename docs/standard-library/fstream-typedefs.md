---
title: '&lt;fstream —&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: fc87e3182e0ee1c8cb4079dd411f54dff0b4c993
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846782"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream —&gt; definicje typów

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Typ `basic_filebuf` specjalne na `char` parametrów szablonu.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md), wyspecjalizowany dla elementów typu `char` z domyślnego cech znaków.

## <a name="fstream"></a>  fstream —

Typ `basic_fstream` specjalne na `char` parametrów szablonu.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_fstream —](../standard-library/basic-fstream-class.md), wyspecjalizowany dla elementów typu `char` z domyślnego cech znaków.

## <a name="ifstream"></a>  ifstream

Definiuje strumienia ma być używany do odczytu danych znaków jednobajtowych szeregowe z pliku. `ifstream` element typedef, który specjalizuje się klasy szablonu jest `basic_ifstream` dla `char`.

Istnieje również `wifstream`, element typedef, który specjalizuje się `basic_ifstream` odczytać `wchar_t` podwójnej szerokości znaków. Aby uzyskać więcej informacji, zobacz [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ifstream —](../standard-library/basic-ifstream-class.md), wyspecjalizowany elementów typu char o cechach znak domyślny. Na przykład

`using namespace std;`

`ifstream infile("existingtextfile.txt");`

`if (!infile.bad())`

`{`

`// Dump the contents of the file to cout.`

`cout << infile.rdbuf();`

`infile.close();`

`}`

## <a name="ofstream"></a>  ofstream

Typ `basic_ofstream` specjalne na `char` parametrów szablonu.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ofstream —](../standard-library/basic-ofstream-class.md), wyspecjalizowany dla elementów typu `char` z domyślnego cech znaków.

## <a name="wfstream"></a>  wfstream

Typ `basic_fstream` specjalne na `wchar_t` parametrów szablonu.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_fstream —](../standard-library/basic-fstream-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.

## <a name="wifstream"></a>  wifstream

Typ `basic_ifstream` specjalne na `wchar_t` parametrów szablonu.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ifstream —](../standard-library/basic-ifstream-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.

## <a name="wofstream"></a>  wofstream

Typ `basic_ofstream` specjalne na `wchar_t` parametrów szablonu.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ofstream —](../standard-library/basic-ofstream-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.

## <a name="wfilebuf"></a>  wfilebuf

Typ `basic_filebuf` specjalne na `wchar_t` parametrów szablonu.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.

## <a name="see-also"></a>Zobacz także

[\<fstream>](../standard-library/fstream.md)<br/>
