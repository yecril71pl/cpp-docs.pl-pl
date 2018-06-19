---
title: Podstawowe typy (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0da64edaa3f94ac9813408d936e3f83783e6b241
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098540"
---
# <a name="fundamental-types-ccx"></a>Podstawowe typy (C + +/ CX)
Oprócz standardowych C++ wbudowanych typów, C + +/ CX obsługuje system typu, który jest definiowana za pomocą architektury środowiska wykonawczego systemu Windows, zapewniając definicje typów dla podstawowych środowiska wykonawczego systemu Windows typy, które odpowiadają typom standard C++. C + +/ CX implementuje wartość logiczna, znaków i typy podstawowe liczbowe. Te definicje typów zdefiniowanych w `default` przestrzeni nazw, które nigdy nie musi być jawnie określona. Ponadto C + +/ CX udostępnia konkretnych implementacji i otoki dla niektórych typów środowiska wykonawczego systemu Windows i interfejsów.  
  
## <a name="boolean-and-character-types"></a>Typy Boolean i znaku  
 W poniższej tabeli wymieniono wbudowanych logicznych i typy znaków i odpowiedniki standard C++.  
  
|Przestrzeń nazw|C + +/ CX nazwy|Definicja|Standardowa nazwa C++|Wartości zakresu|  
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|Platforma|Boolean|8-bitową wartość logiczna.|bool|`true` (niezerowej) i `false` (zero).|  
|default|char16|Wartość nieliczbowy 16-bitowego, która reprezentuje punkt kodu Unicode (UTF-16).|wchar_t<br /><br /> —lub—<br /><br /> L'c "|(Określony w standardzie Unicode)|  
  
## <a name="numeric-types"></a>Typy liczbowe  
 Poniższa lista zawiera wbudowane typy liczbowe. Numeryczne typy są zadeklarowane w `default` przestrzeni nazw i czy definicje typów dla danego typu wbudowanego C++. Nie wszystkie (długi, na przykład) typy wbudowane C++ są obsługiwane w środowisku wykonawczym systemu Windows. Zachowanie spójności i przejrzystości, firma Microsoft zaleca użycie C + +/ CX nazwy.  
  
|C + +/ CX nazwy|Definicja|Standardowa nazwa C++|Wartości zakresu|  
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|int8|8-bitową podpisem wartość liczbowa.|char podpisem|-128 do 127|  
|uint8|8-bitowych unsigned wartość liczbowa.|unsigned char|0 do 255|  
|Int16|16-bitową liczbę całkowitą ze znakiem.|short|-32 768 do 32 767|  
|UInt16|16-bitową liczbę całkowitą bez znaku.|unsigned short|od 0 do 65 535|  
|int32|Całkowita 32-bitowych.|int|-2,147,483,648 do 2 147 483 647|  
|uint32|32-bitowa liczba całkowita bez znaku.|unsigned int|od 0 do 4 294 967 295|  
|int64|Całkowita 64-bitowych.|długie long - lub - __int64|-9,223,372,036,854, 775,808 za pośrednictwem 9,223,372,036,854,775,807|  
|uint64|64-bitowa liczba całkowita bez znaku.|niepodpisane __int64 długo długo - lub - bez znaku|od 0 do 18,446,744,073,709,551,615|  
|Float32|Liczba zmiennoprzecinkowa IEEE-754 32-bitowa.|float|3.4e +/-38 (7 cyfr)|  
|Float64|Liczby zmiennoprzecinkowej IEEE-754 64-bitowe.|double|1.7e +/-308 (15 cyfr)|  
  
## <a name="windows-runtime-types"></a>Typy środowiska wykonawczego systemu Windows  
 W poniższej tabeli wymieniono niektóre dodatkowe typy definiowane przez architekturę środowiska wykonawczego systemu Windows, które są wbudowane w języku C + +/ CX. Obiekt i ciąg są typy referencyjne. Są inne typy wartości. Wszystkie te typy są zadeklarowane w `Platform` przestrzeni nazw. Aby uzyskać pełną listę, zobacz [przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md).  
  
|Nazwa|Definicja|  
|----------|----------------|  
|Obiekt|Reprezentuje dowolny typ środowiska uruchomieniowego systemu Windows.|  
|String|Ciąg znaków, które reprezentują tekstu.|  
|Rect|Zestaw czterech liczb zmiennoprzecinkowych, reprezentujące lokalizacja i rozmiar prostokąta.|  
|SizeT|Para uporządkowanych liczb zmiennoprzecinkowych, która określa wysokość i szerokość.|  
|punkt|Para uporządkowanej zmiennoprzecinkowe współrzędne x i y współrzędnych definiujące punkt w dwuwymiarowego rzutu.|  
|Identyfikator GUID|Wartość nieliczbowy 128-bitowego, która jest używana jako unikatowy identyfikator.|  
|UIntPtr|(Tylko do użytku wewnętrznego.) Bez znaku wartość 64-bitowego, która jest używana jako wskaźnik.|  
|IntPtr|(Tylko do użytku wewnętrznego.)  Podpisem wartość 64-bitowych, która jest używana jako wskaźnik.|  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)