---
title: Właściwości projektu kopiowania źródeł (Linux C++)
ms.date: 10/16/2019
ms.assetid: 1a44230d-5dd8-4d33-93b4-e77e03e00150
ms.openlocfilehash: ceaa1240f08b83ebc83bd7fdc25a3215467eb3f1
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444946"
---
# <a name="copy-sources-project-properties-linux-c"></a>Właściwości projektu kopiowania źródeł (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Właściwości ustawione na tej stronie właściwości mają zastosowanie do wszystkich plików w projekcie, z wyjątkiem tego, których właściwości na poziomie plików są ustawione.

Właściwość | Opis
--- | ---
Źródła do skopiowania | Określa źródła do skopiowania do systemu zdalnego. Zmiana tej listy może zmienić się lub w inny sposób mieć wpływ na strukturę katalogów, w której pliki są kopiowane do systemu zdalnego.
Kopiuj źródła | Określa, czy źródła mają być kopiowane do systemu zdalnego.
Dodatkowe źródła do skopiowania | Określa dodatkowe źródła do skopiowania do systemu zdalnego. Opcjonalnie listę można dostarczyć jako lokalną do zdalnych par mapowania przy użyciu składni podobnej do następującej: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym.

@SourcesToCopyRemotely i @DataFilesToCopyRemotely odwołują się do grup elementów w pliku projektu. Aby zmodyfikować źródła lub pliki danych, które są kopiowane zdalnie, edytuj plik *vcxproj* w następujący sposób:

```xml
<ItemGroup>
   <MyItems Include=“foo.txt” />
   <MyItems Include=“bar.txt” />
   <DataFilesToCopyRemotely Include=”@(MyItems)” />
</ItemGroup>
```

::: moniker-end
