---
title: Typy podstawowe (C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 3d484d9490a0a5b2ee2e7f92381528124b47701c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231003"
---
# <a name="fundamental-types-ccx"></a>Typy podstawowe (C++/CX)

Oprócz standardowych typów wbudowanych języka C++/CX języka C++ obsługuje system typów, który jest zdefiniowany przez architekturę środowisko wykonawcze systemu Windows, dostarczając elementy typedef dla typów podstawowych środowisko wykonawcze systemu Windows, które są mapowane na standardowe typy języka C++. C++/CX implementuje wartości logiczne, znakowe i liczbowe podstawowe typy. Te definicje typów są zdefiniowane w `default` przestrzeni nazw, która nigdy nie musi być określona jawnie. Ponadto C++/CX zapewnia otoki i konkretne implementacje dla niektórych typów środowisko wykonawcze systemu Windows i interfejsów.

## <a name="boolean-and-character-types"></a>Typy logiczne i znaki

Poniższa tabela zawiera listę wbudowanych typów wartości logicznych i znaków oraz ich standardowych odpowiedników języka C++.

|Przestrzeń nazw|Nazwa/CX języka C++|Definicja|Standardowa nazwa języka C++|Zakres wartości|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|Platforma|Wartość logiczna|8-bitowa wartość logiczna.|bool|**`true`**(niezerowe) i **`false`** (zero)|
|default|char16|16-bitowa wartość nieliczbowa, która reprezentuje punkt kodowy Unicode (UTF-16).|wchar_t<br /><br /> -lub-<br /><br /> L'c'|(Określony przez standard Unicode)|

## <a name="numeric-types"></a>Typy liczbowe

Poniższa tabela zawiera listę wbudowanych typów liczbowych. Typy liczbowe są deklarowane w `default` przestrzeni nazw i są typedef dla odpowiedniego typu wbudowanego języka C++. Nie wszystkie typy wbudowane języka C++ (na przykład) są obsługiwane w środowisko wykonawcze systemu Windows. Aby zapewnić spójność i przejrzystość, zalecamy użycie nazwy/CX języka C++.

|Nazwa/CX języka C++|Definicja|Standardowa nazwa języka C++|Zakres wartości|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|Int8|8-bitowa podpisana wartość numeryczna.|znak ze znakiem|-128 do 127|
|Uint8|8-bitowa wartość liczbowa bez znaku.|unsigned char|od 0 do 255|
|Int16|16-bitowa liczba całkowita ze znakiem.|short|-32 768 do 32 767|
|UInt16|16-bitowa liczba całkowita bez znaku.|unsigned short|od 0 do 65 535|
|elementem|32-bitowa liczba całkowita ze znakiem.|int|-2 147 483 648 do 2 147 483 647|
|równ|32-bitowa liczba całkowita bez znaku.|unsigned int|od 0 do 4 294 967 295|
|Int64|64-bitowa liczba całkowita ze znakiem.|Long Long-lub-__int64|-9 223 372 036 854, 775 808 do 9 223 372 036 854 775 807|
|UInt64|64-bitowa liczba całkowita bez znaku.|__int64 bez znaku long long-lub-unsigned|od 0 do 18446744073709551615 są|
|float32|32-bitowa liczba zmiennoprzecinkowa IEEE 754.|float|3.4 e +/-38 (7 cyfr)|
|Float64|64-bitowa liczba zmiennoprzecinkowa IEEE 754.|double|1.7 e +/-308 (15 cyfr)|

## <a name="windows-runtime-types"></a>Typy środowisko wykonawcze systemu Windows

W poniższej tabeli wymieniono niektóre dodatkowe typy, które są zdefiniowane przez architekturę środowisko wykonawcze systemu Windows i są wbudowane w C++/CX. Obiekt i ciąg są typami referencyjnymi. Pozostałe są typami wartości. Wszystkie te typy są zadeklarowane w `Platform` przestrzeni nazw. Aby uzyskać pełną listę, zobacz [przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md).

|Nazwa|Definicja|
|----------|----------------|
|Obiekt|Reprezentuje dowolny typ środowisko wykonawcze systemu Windows.|
|String|Ciąg znaków, który reprezentuje tekst.|
|Rect|Zestaw czterech liczb zmiennoprzecinkowych, które reprezentują lokalizację i rozmiar prostokąta.|
|SizeT|Uporządkowana para liczb zmiennoprzecinkowych, które określają wysokość i szerokość.|
|Moment|Uporządkowana para zmiennoprzecinkowych współrzędnych x i Współrzędne y, które definiują punkt w płaszczyźnie dwuwymiarowej.|
|Guid (identyfikator GUID)|128-bitowa wartość nieliczbowa, która jest używana jako unikatowy identyfikator.|
|UIntPtr|(Tylko do użytku wewnętrznego). Nieniepodpisana wartość 64-bitowa, która jest używana jako wskaźnik.|
|IntPtr|(Tylko do użytku wewnętrznego).  Podpisana wartość 64-bitowa, która jest używana jako wskaźnik.|

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)
