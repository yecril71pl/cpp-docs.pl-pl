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
ms.openlocfilehash: b77c778017dc78235948e8d23db136c1f63ab12d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372438"
---
# <a name="bind"></a>/BIND
```  
/BIND[:PATH=path]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja umożliwia ustawienie adresy punktów wejścia w tabelę adresów importu dla pliku wykonywalnego lub DLL. Użyj tej opcji, aby skrócić czas obciążenia programu.  
  
 Określ plik wykonywalny programu i bibliotek DLL w *pliki* argument w wierszu polecenia EDITBIN polecenia. Opcjonalny *ścieżki* argument /BIND Określa lokalizację biblioteki DLL używane przez określonych plików. Oddziel wiele katalogów średnikami (**;**). Jeśli *ścieżka* nie zostanie określony, polecenia EDITBIN wyszukuje katalogi określone w zmiennej środowiskowej PATH. Jeśli *ścieżki* określono polecenia EDITBIN ignoruje zmiennej PATH.  
  
 Domyślnie program ładujący ustawia adresy punktów wejścia ładuje programu. Ilość czasu, przez ten proces trwa różni się w zależności od liczby bibliotek DLL i liczbę punktów wejścia, do którego odwołuje się ten program. Jeśli program został zmodyfikowany z /BIND i podstawowym adresy dla pliku wykonywalnego i jego biblioteki DLL nie powodują konfliktów z bibliotek DLL, które już są załadowane, system operacyjny nie trzeba ustawić tych adresów. W sytuacji, gdy pliki są niepoprawnie na podstawie system operacyjny przenosi bibliotek DLL programu i ponownie oblicza adresy punktu wejścia, który dodaje do czasu ładowania programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje EDITBIN](../../build/reference/editbin-options.md)