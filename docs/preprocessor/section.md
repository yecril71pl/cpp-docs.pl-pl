---
title: section, pragma
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 47ae2ff2503317e937e2b3a497357afbd5522a64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216602"
---
# <a name="section-pragma"></a>section, pragma

Tworzy sekcję w pliku. obj.

## <a name="syntax"></a>Składnia

> **sekcja #pragma (** "*sekcja-Name*" [ **,** *Attributes* ] **)**

## <a name="remarks"></a>Uwagi

*Segment* terminów i *sekcja* mają takie samo znaczenie w tym artykule.

Po zdefiniowaniu sekcji pozostaje ona ważna dla pozostałej części kompilacji. Należy jednak użyć [__declspec (allocate)](../cpp/allocate.md)lub nic nie jest umieszczane w sekcji.

*Nazwa sekcji* jest wymaganym parametrem, który zmienia nazwę sekcji. Nazwa nie może powodować konfliktu z nazwami sekcji standardowych. Zobacz [/Section](../build/reference/section-specify-section-attributes.md) , aby uzyskać listę nazw, których nie należy używać podczas tworzenia sekcji.

*atrybuty* to opcjonalny parametr składający się z co najmniej jednego atrybutu rozdzielanego przecinkami do przypisania do sekcji. Możliwe *atrybuty* :

|Atrybut|Opis|
|-|-|
|**read**|Zezwala na operacje odczytu danych.|
|**write**|Zezwala na operacje zapisu w danych.|
|**execute**|Zezwala na wykonanie kodu.|
|**udostępniać**|Udostępnia sekcję wśród wszystkich procesów, które ładują obraz.|
|**nopage**|Oznacza sekcję jako niestronicowaną. Przydatne w przypadku sterowników urządzeń Win32.|
|**nocache**|Oznacza sekcję jako niebędącą w pamięci podręcznej. Przydatne w przypadku sterowników urządzeń Win32.|
|**odrzucone**|Oznacza sekcję jako odrzucony. Przydatne w przypadku sterowników urządzeń Win32.|
|**remove**|Oznacza sekcję jako niebędącą rezydentem pamięci. Dotyczy tylko sterowników urządzeń wirtualnych (V*x*D).|

Jeśli nie określisz żadnych atrybutów, sekcja ma atrybuty **Odczyt** i **zapis** .

## <a name="example"></a>Przykład

W tym przykładzie pierwsza sekcja pragma identyfikuje sekcję i jej atrybuty. Liczba całkowita `j` nie jest `mysec` umieszczana, ponieważ nie została zadeklarowana `__declspec(allocate)`przy użyciu. Zamiast tego `j` przechodzą do sekcji dane. Liczba całkowita `i` jest w `mysec` wyniku `__declspec(allocate)` atrybutu klasy magazynu.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
