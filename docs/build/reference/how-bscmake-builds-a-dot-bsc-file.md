---
title: "Jaki sposób BSCMAKE kompiluje. Pliku BSC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb8e03bed85a5e466a3c41f0cffc51d35c4b4561
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-bscmake-builds-a-bsc-file"></a>W jaki sposób BSCMAKE kompiluje plik .Bsc
BSCMAKE kompiluje lub odtwarza pliku .bsc w najbardziej wydajny sposób, może on. Aby uniknąć potencjalnych problemów, ważne jest zrozumienie procesu kompilacji.  
  
 Gdy BSCMAKE kompiluje plik informacji przeglądania, obcina pliki SBR na zero, długość. Podczas kolejnych kompilacji tego samego pliku plik .sbr o zerowej długości (lub wartość null) informuje BSCMAKE czy plik .sbr ma nie nowy udział, aby. Pozwala on usłudze BSCMAKE wiedział, że aktualizacja części pliku nie jest wymagana, a wzrostowe będą wystarczające. Podczas każdej kompilacji (o ile nie określono opcji /n), BSCMAKE najpierw próbuje zaktualizować pliku przyrostowo przy użyciu tylko te pliki SBR, które zostały zmienione.  
  
 BSCMAKE szuka pliku .bsc o nazwie określona z opcją /o. Jeśli nie określono /o, BSCMAKE szuka pliku o nazwie podstawowej pierwszy plik SBR i rozszerzenia .bsc. Jeśli plik istnieje, BSCMAKE wykonuje wzrostowe pliku informacyjnego przeglądarki przy użyciu tylko uczestniczących pliki .sbr. Jeśli plik nie istnieje, BSCMAKE wykonuje przy użyciu wszystkich plików SBR pełnej kompilacji. Dostępne są następujące reguły dla kompilacji:  
  
-   Dla pełnej kompilacji została wykonana pomyślnie wszystkie określone pliki SBR musi istnieć i nie musi być obcięte. Jeśli plik .sbr został obcięty, należy ponownie zbudować go (przy ponownej kompilacji lub budowanie) przed uruchomieniem BSCMAKE.  
  
-   Dla kompilacji przyrostowej powiodła się musi istnieć w pliku .bsc. Wszystkie pliki SBR uczestniczących, nawet pustych plików, musi istnieć i musi być określona w wierszu polecenia BSCMAKE. W przypadku pominięcia pliku .sbr z wiersza polecenia, BSCMAKE usuwa swojego wkładu z pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie pliku .Bsc](../../build/reference/building-a-dot-bsc-file.md)