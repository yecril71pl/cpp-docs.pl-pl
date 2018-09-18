---
title: Magazynowanie i wyrównanie struktur | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 867b549575847a59f7d1e8a61792c8b097383a10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092833"
---
# <a name="storage-and-alignment-of-structures"></a>Magazynowanie i wyrównanie struktur

**Microsoft Specific**

Elementy członkowskie struktur są przechowywane sekwencyjnie, w kolejności, w której były zadeklarowane: pierwszy element członkowski ma najniższy adres pamięci, a ostatni element członkowski – najwyższy.

Każdy obiekt danych posiada *wymóg wyrównania*. W przypadku struktur, wymagany jest największy z ich elementów członkowskich. Każdemu obiektowi przypisany *przesunięcie* tak, aby

*Przesunięcie* `%` *wymóg wyrównania* `==` 0

Sąsiadujące pola bitowe są pakowane w takie same 1-, 2- lub 4-bajtowe jednostki alokacji, jeśli typy całkowite mają taki sam rozmiar i jeśli następne pole bitowe pasuje do bieżącej jednostki alokacji bez przekraczania granicy nałożonej przez wspólne wymagania wyrównania pól bitowych.

Aby zaoszczędzić miejsce lub zachować zgodność z istniejącymi strukturami danych, możesz chcieć przechowywać struktury w mniej lub bardziej kompaktowy sposób. [/ZP](../build/reference/zp-struct-member-alignment.md)[*n*] — opcja kompilatora i [#pragma pack](../preprocessor/pack.md) kontrolki, w jaki dane struktury są "pakowane" do pamięci. Kiedy używasz/ZP [*n*] opcji, gdzie *n* to 1, 2, 4, 8 lub 16, każdy element członkowski struktury po pierwszym jest przechowywany na bajt granic, które są albo wymaganym wyrównaniem pola, albo pakowanie rozmiaru ( *n*), która kwota jest mniejsza. Wyrażone jako formuła, granice bajtowe są

```
min( n, sizeof( item ) )
```

gdzie *n* jest rozmiarem pakowania wyrażonym z/ZP [*n*] opcji i *elementu* jest elementem członkowskim struktury. Domyślny rozmiar pakowania to /Zp8.

Aby użyć dyrektywy `pack` do określenia pakowania innego, niż określone w wierszu polecenia dla określonej struktury, przed strukturą podaj dyrektywę `pack`, gdzie rozmiar pakowania wynosi 1, 2, 4, 8 lub 16. Aby przywrócić pakowanie podane w wierszu polecenia, określ dyrektywę `pack` bez argumentów.

Domyślny rozmiar pól bitowych **długie** dla kompilatora C firmy Microsoft. Elementy członkowskie struktury są wyrównane do rozmiaru typu lub/ZP [*n*] rozmiar, która kwota jest mniejsza. Domyślny rozmiar to 4.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaracje struktur](../c-language/structure-declarations.md)