---
title: Właściwości projektu Kopiuj źródła (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: 732a13520a223f1aa73733cd4098c247052f8d3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441390"
---
# <a name="copy-sources-project-properties-linux-c"></a>Właściwości projektu Kopiuj źródła (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Właściwości ustawione na tej stronie właściwości dotyczą wszystkich plików w projekcie, z wyjątkiem których właściwości na poziomie pliku są ustawione.

| Właściwość | Opis |
|--|--|
| Źródła do skopiowania | Określa źródła do skopiowania do systemu zdalnego. Zmiana tej listy może zostać przesunięta lub w inny sposób wpłynąć na strukturę katalogów, do której pliki są kopiowane w systemie zdalnym. |
| Kopiuj źródła | Określa, czy źródła mają być kopiowane do systemu zdalnego. |
| Dodatkowe źródła do skopiowania | Określa dodatkowe źródła do skopiowania do systemu zdalnego. Opcjonalnie należy określić lokalne i zdalne pary mapowania przy użyciu składni w ten sposób: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, gdzie plik lokalny może być skopiowany do określonej lokalizacji zdalnej w systemie zdalnym. |

@SourcesToCopyRemotelyi @DataFilesToCopyRemotely odnoszą się do grup elementów w pliku projektu. Aby zmodyfikować źródła lub pliki danych są kopiowane zdalnie, edytuj plik *vcxproj* w ten sposób:

```xml
<ItemGroup>
   <MyItems Include="foo.txt" />
   <MyItems Include="bar.txt" />
   <DataFilesToCopyRemotely Include="@(MyItems)" />
</ItemGroup>
```

::: moniker-end
