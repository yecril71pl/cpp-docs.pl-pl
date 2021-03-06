---
title: W jaki sposób BSCMAKE kompiluje plik .Bsc
ms.date: 11/04/2016
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
ms.openlocfilehash: 6f721641e021396f112bfe4c075ca0f524100d1f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291161"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>W jaki sposób BSCMAKE kompiluje plik .Bsc

BSCMAKE kompiluje lub ponownie kompiluje plik .bsc w najbardziej efektywny sposób, w których jest to możliwe. Aby uniknąć potencjalnych problemów, ważne jest zrozumienie procesu kompilacji.

Gdy BSCMAKE kompiluje plik informacji przeglądania, obcina .SBR — pliki do zera długości. Podczas kolejnych kompilacji tego samego pliku plik SBR o zerowej długości (lub jest pusty) informuje o tym BSCMAKE czy plik .sbr nie ma żadnych nowych wkład się. Dzięki temu BSCMAKE wiedzieć, że aktualizacja tę część pliku nie jest wymagana, a kompilacja przyrostowa okażą się wystarczające. Podczas każdej kompilacji (o ile nie określono opcji /n), BSCMAKE najpierw próbuje zaktualizować plik przyrostowo za pomocą tylko te pliki SBR, które zostały zmienione.

BSCMAKE szuka pliku .bsc, który ma określoną opcją /o nazwę. Jeśli nie określono /o, BSCMAKE szuka pliku, który ma nazwę podstawową pierwszy plik SBR i rozszerzenie .bsc. Jeśli plik istnieje, BSCMAKE wykonuje wzrostowe pliku informacyjnego przeglądarki przy użyciu tylko powiązanych plików SBR. Jeśli plik nie istnieje, BSCMAKE wykonuje pełna kompilacja za pomocą wszystkich plików SBR. Reguły dla kompilacji są następujące:

- Dla pełnej kompilacji zakończyło się sukcesem wszystkie określone pliki SBR, musi istnieć i nie jest obcięty. Jeśli plik SBR jest przycięty, należy odbudować go (przy ponownej kompilacji lub budowanie), przed uruchomieniem BSCMAKE.

- Kompilacja przyrostowa zakończyło się sukcesem musi istnieć pliku .bsc. Wszystkich powiązanych plików SBR nawet pustych plików, musi istnieć i musi zostać określony w wierszu polecenia BSCMAKE. Jeżeli pominięto plik SBR z wiersza polecenia BSCMAKE usuwa swój wkład zgodnie z pliku.

## <a name="see-also"></a>Zobacz także

[Kompilowanie pliku .Bsc](building-a-dot-bsc-file.md)
