---
title: Typy podstawowe (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e30e7ced4f4e761f7342811c533c1f361d0b1df
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754198"
---
# <a name="fundamental-types-ccx"></a>Typy podstawowe (C + +/ CX)
Oprócz standardowych wbudowanych typów C++, C + +/ CX obsługuje system typu, który jest definiowany przez architekturę środowiska wykonawczego Windows, zapewniając definicje typów dla środowiska uruchomieniowego Windows podstawowych typów mapowane na typy języka C++ standard... C + +/ CX implementuje wyrażenie logiczne, znaki i liczbowych typów podstawowych. Te definicje typów są zdefiniowane w `default` przestrzeń nazw, która nigdy nie musi być jawnie określony. Ponadto, C + +/ CX zapewnia otoki i konkretnych implementacji niektórych interfejsów i typów środowiska wykonawczego Windows.  
  
## <a name="boolean-and-character-types"></a>Typy Boolean i znaków  
 Poniższa lista zawiera wbudowane Boolean i typy znakowe i odpowiedniki standardowego języka C++.  
  
|Przestrzeń nazw|C + +/ CX nazwy|Definicja|Nazwa czasu standardowego języka C++|Zakres wartości|  
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|Platforma|Boolean|Wartość logiczna 8-bitowych.|bool|`true` (niezerową) i `false` (zero)|  
|default|char16|Wartość nieliczbową 16-bitową, która reprezentuje punkt kodu Unicode (UTF-16).|wchar_t<br /><br /> —lub—<br /><br /> L'c "|(Określony przez Unicode standard)|  
  
## <a name="numeric-types"></a>Typy liczbowe  
 Poniższa tabela zawiera listę wbudowanych typów liczbowych. Typy liczbowe są deklarowane w `default` przestrzeni nazw i czy definicje typów dla danego typu wbudowanego C++. Nie wszystkie C++ wbudowanych typów (long, na przykład) są obsługiwane w środowisku uruchomieniowym Windows. Zachowanie spójności i przejrzystości, firma Microsoft zaleca użycie C + +/ CX nazwy.  
  
|C + +/ CX nazwy|Definicja|Nazwa czasu standardowego języka C++|Zakres wartości|  
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|int8|8-bitowe podpisane wartość liczbowa.|podpisany char|od -128 do 127|  
|uint8|8-bitową wartością numeryczną bez znaku.|unsigned char|od 0 do 255|  
|Int16|Całkowita 16-bitowych.|short|-32 768 do 32 767|  
|UInt16|16-bitowa liczba całkowita bez znaku.|unsigned short|od 0 do 65 535|  
|int32|Całkowita 32-bitowych.|int|-2,147,483,648 do 2 147 483 647|  
|uint32|32-bitowa liczba całkowita bez znaku.|unsigned int|od 0 do 4 294 967 295|  
|int64|Całkowita 64-bitowych.|Long long - lub - __int64|-9,223,372,036,854, 775,808 za pośrednictwem 9,223,372,036,854,775,807|  
|uint64|64-bitowej nieoznaczonej liczby całkowitej.|unsigned long long - lub - unsigned __int64|od 0 do 18,446,744,073,709,551,615|  
|float32|Liczba zmiennoprzecinkowa IEEE 754 32-bitowych.|float|3.4e/38 (7 cyfr)|  
|float64|Liczba zmiennoprzecinkowa IEEE 754 64-bitowych.|double|308 (15 cyfr) 1, 7e|  
  
## <a name="windows-runtime-types"></a>Typów środowiska wykonawczego Windows  
 W poniższej tabeli wymieniono niektóre dodatkowe typy są definiowane przez architekturę środowiska wykonawczego Windows, które są wbudowane w języku C + +/ CX. Obiekt i parametry są typami odwołań. Inne są typami wartości. Wszystkie te typy są deklarowane w `Platform` przestrzeni nazw. Aby uzyskać pełną listę, zobacz [przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md).  
  
|Nazwa|Definicja|  
|----------|----------------|  
|Obiekt|Reprezentuje dowolny typ środowiska wykonawczego Windows.|  
|String|Ciąg znaków, które reprezentują tekstu.|  
|Rect|Zestaw czterech liczb zmiennoprzecinkowych, które reprezentują położenie i rozmiar prostokąta.|  
|SizeT|Uporządkowana para liczb zmiennoprzecinkowych, który określa szerokość i wysokość.|  
|Punkt|Uporządkowana para zmiennoprzecinkowych współrzędnych x i współrzędne y, które definiują punkt w dwuwymiarowej płaszczyzny.|  
|Identyfikator GUID|Wartość nieliczbową 128-bitowego, która jest używana jako unikatowy identyfikator.|  
|UIntPtr|(Tylko do użytku wewnętrznego.) Niepodpisane wartość 64-bitową, która jest używana jako wskaźnik.|  
|Pola IntPtr|(Tylko do użytku wewnętrznego.)  Podpisany wartość 64-bitową, która jest używana jako wskaźnik.|  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)