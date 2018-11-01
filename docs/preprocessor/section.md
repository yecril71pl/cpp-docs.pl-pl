---
title: sekcja
ms.date: 11/04/2016
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: cd8eee564fa17b21d5421a3471fd676af921f444
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462143"
---
# <a name="section"></a>sekcja

Tworzy sekcję w pliku .obj.

## <a name="syntax"></a>Składnia

```
#pragma section( "section-name" [, attributes] )
```

## <a name="remarks"></a>Uwagi

Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.

Po zdefiniowaniu sekcji pozostaje prawidłowe na pozostałą część kompilacji. Jednakże, należy użyć [__declspec(allocate)](../cpp/allocate.md) lub nic nie zostanie umieszczona w sekcji.

*Nazwa sekcji* jest wymaganym parametrem, który ma być nazwa sekcji. Nazwa nie może powodować konfliktu z nazwami standardowej sekcji. Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) listę nazw, nie należy używać podczas tworzenia sekcji.

*atrybuty* jest parametrem opcjonalnym składający się z co najmniej jeden rozdzielonych przecinkami atrybutów, które chcesz przypisać do sekcji. Możliwe *atrybuty* są:

|Atrybut|Opis|
|-|-|
|**read**|Umożliwia wykonywanie operacji odczytu na danych.|
|**write**|Umożliwia wykonywanie operacji zapisu na danych.|
|**execute**|Umożliwia wykonanie kodu.|
|**Udostępnione**|Udostępnia sekcji między wszystkie procesy, które ładują obrazu.|
|**nopage**|Oznacza sekcji nie stronicowanej; przydatne dla sterowników urządzeń systemu Win32.|
|**nocache**|Oznacza sekcji nie podlega buforowaniu; przydatne dla sterowników urządzeń systemu Win32.|
|**Odrzuć**|Oznacza sekcji discardable; przydatne dla sterowników urządzeń systemu Win32.|
|**remove**|Oznacza sekcji, co nie rezydentnego; sterowniki urządzeń wirtualnych (V*x*D) tylko.|

Jeśli nie określisz atrybutów, sekcji będzie po ich przeczytaniu i Zapis atrybutów.

## <a name="example"></a>Przykład

W poniższym przykładzie pierwsza instrukcja identyfikuje sekcji i jego atrybuty. Liczba całkowita `j` nie są umieszczane w `mysec` , ponieważ nie został zadeklarowany za pomocą `__declspec(allocate)`; `j` przechodzi w sekcji danych. Liczba całkowita `i` konstrukcyjnym `mysec` na jego `__declspec(allocate)` atrybuty klasy magazynu.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)