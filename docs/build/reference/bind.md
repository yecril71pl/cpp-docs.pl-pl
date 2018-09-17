---
title: -BIND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bind
dev_langs:
- C++
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a47004ce41d6bae3d91a81c4a61a712bc31dfbdb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725897"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>Uwagi

Ta opcja umożliwia ustawienie adresy punktów wejścia w tabeli adresów importowania dla pliku wykonywalnego lub biblioteki DLL. Użyj tej opcji, aby skrócić czas ładowania programu.

Określ plik wykonywalny i biblioteki dll w programie *pliki* argument w wierszu polecenia EDITBIN. Opcjonalny *ścieżki* argument /BIND Określa lokalizację biblioteki DLL używane przez określone pliki. Wiele katalogów należy oddzielić średnikami (**;**). Jeśli *ścieżki* nie zostanie określony, EDITBIN przeszukuje katalogi określone w zmiennej środowiskowej PATH. Jeśli *ścieżki* określono EDITBIN ignoruje zmiennej PATH.

Domyślnie moduł ładujący program ustawia adresy punktów wejścia, podczas ładowania programu. Ilość czasu potrzebnego przez ten proces różni się w zależności od szeregu bibliotek DLL i liczbę punktów wejścia, do którego odwołuje się program. Jeśli program został zmodyfikowany z /BIND i base adresów dla pliku wykonywalnego, a jego biblioteki DLL nie wchodzą w konflikt z biblioteki dll, które zostały już załadowane, system operacyjny nie trzeba ustawić te adresy. W sytuacji, w której pliki są niepoprawnie na podstawie system operacyjny przenosi bibliotek DLL programu i ponownie oblicza adresy punktu wejścia, który dodaje do czasu ładowania tego programu.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)