---
title: /BIND
ms.date: 11/04/2016
f1_keywords:
- /bind
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
ms.openlocfilehash: e8ba0a5f0235c8771567e4e43172bdf8c81c99a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295035"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>Uwagi

Ta opcja umożliwia ustawienie adresy punktów wejścia w tabeli adresów importowania dla pliku wykonywalnego lub biblioteki DLL. Użyj tej opcji, aby skrócić czas ładowania programu.

Określ plik wykonywalny i biblioteki dll w programie *pliki* argument w wierszu polecenia EDITBIN. Opcjonalny *ścieżki* argument /BIND Określa lokalizację biblioteki DLL używane przez określone pliki. Wiele katalogów należy oddzielić średnikami (**;**). Jeśli *ścieżki* nie zostanie określony, EDITBIN przeszukuje katalogi określone w zmiennej środowiskowej PATH. Jeśli *ścieżki* określono EDITBIN ignoruje zmiennej PATH.

Domyślnie moduł ładujący program ustawia adresy punktów wejścia, podczas ładowania programu. Ilość czasu potrzebnego przez ten proces różni się w zależności od szeregu bibliotek DLL i liczbę punktów wejścia, do którego odwołuje się program. Jeśli program został zmodyfikowany z /BIND i base adresów dla pliku wykonywalnego, a jego biblioteki DLL nie wchodzą w konflikt z biblioteki dll, które zostały już załadowane, system operacyjny nie trzeba ustawić te adresy. W sytuacji, w której pliki są niepoprawnie na podstawie system operacyjny przenosi bibliotek DLL programu i ponownie oblicza adresy punktu wejścia, który dodaje do czasu ładowania tego programu.

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](editbin-options.md)
