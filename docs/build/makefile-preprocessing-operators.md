---
title: "Przetwarzanie wstępne operatorów pliku makefile | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d2d8aa3d428b45da81b2f9256988e089f121dd0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="makefile-preprocessing-operators"></a>Operatory przetwarzania wstępnego pliku reguł programu Make
Pliku reguł programu make przetwarzania wstępnego wyrażenia można używać operatorów, które działają na stałych kody wyjścia z poleceń, ciągi makra i ścieżki systemu plików. Można oszacować wyrażenia, preprocesora najpierw rozszerza makra, a następnie wykonuje polecenia, a następnie wykonuje operacje. Operacje są oceniane według grupowanie jawne w nawiasy, a następnie według kolejność wykonywania działań. Wynik jest wartością stałą.  
  
 `DEFINED` Operator to operator logiczny, który działa na nazwę makra. Wyrażenie `DEFINED(` *makra* `)` ma wartość true Jeśli *makra* jest zdefiniowany, nawet jeśli nie ma przypisanej wartości. `DEFINED`w połączeniu z `!IF` lub `!ELSE IF` jest odpowiednikiem `!IFDEF` lub `!ELSE IFDEF`. Jednak w przeciwieństwie do tych dyrektyw `DEFINED` mogą być używane w złożonych wyrażeń.  
  
 `EXIST` Operator to operator logiczny, który działa na ścieżki systemu plików. `EXIST(`*ścieżka* `)` ma wartość true Jeśli *ścieżki* istnieje. Wynik `EXIST` można używać w wyrażeniach binarnego. Jeśli *ścieżki* zawiera spacje, ujmij ją w podwójny cudzysłów.  
  
 Aby porównać dwa ciągi, użyj równości (`==`) operator lub nierówności (`!=`) operatora. Ciągi należy ująć w podwójny cudzysłów.  
  
 Stałe całkowite umożliwiają operatory jednoargumentowe Negacja wartości liczbowych (`-`), co do uzupełnienia (`~`), a logiczny negacji (`!`).  
  
 Wyrażenia można użyć następujących operatorów. Operatory równy priorytet są grupowane i grup są wymienione w kolejności malejącej. Operatory jednoargumentowe skojarzyć z argumentem w prawo. Operatory binarne pierwszeństwa równy skojarzyć operandy od lewej do prawej.  
  
|Operator|Opis|  
|--------------|-----------------|  
|`DEFINED(`*makra*`)`|Tworzy wartość logiczną dla bieżącego stanu definicji *makra*.|  
|`EXIST(`*ścieżki*`)`|Tworzy wartość logiczną istnienie w pliku *ścieżki*.|  
|||  
|`!`|NEGACJA jednoargumentowy.|  
|`~`|Uzupełnienie jednoargumentowy osoby.|  
|`-`|Negacja jednoargumentowy.|  
|||  
|`*`|Mnożenia.|  
|`/`|Podział.|  
|`%`|Modułu (reszty).|  
|||  
|`+`|Dodatek.|  
|`-`|Odejmowanie.|  
|||  
|`<<`|Operatory przesunięcia w lewo.|  
|`>>`|Bitowe przesunięcia w prawo.|  
|||  
|`<=`|Mniejsze niż lub równe.|  
|`>=`|Większe lub równe.|  
|`<`|Poniżej.|  
|`>`|Większa.|  
|||  
|`==`|Równości.|  
|`!=`|Nierówności.|  
|||  
|`&`|Bitowe koniunkcji binarnej.|  
|`^`|Iloczynu bitowego XOR.|  
|`&#124;`|Wartość logiczną lub.|  
|||  
|`&&`|Operatora logicznego AND.|  
|||  
|`&#124;&#124;`|Operatora logicznego OR.|  
  
> [!NOTE]
>  Bitowy operator XOR (`^`) jest taka sama jak znak ucieczki i należy zastosować ucieczkę (jako `^^`) gdy jest używana w wyrażeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w przetwarzaniu wstępnym pliku reguł programu make](../build/expressions-in-makefile-preprocessing.md)