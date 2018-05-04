---
title: -STERCIE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /heap
dev_langs:
- C++
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5306df647801d7d1467aa0f44bfacca18fccaff3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="heap"></a>/HEAP
Ustawia rozmiar sterty w bajtach. Ta opcja ma zastosowanie tylko do plików wykonywalnych.  
  
```  
  
/HEAP:  
reserve[,commit]  
```  
  
## <a name="remarks"></a>Uwagi  
 `reserve` Argument określa Alokacja całkowita początkowej sterty w pamięci wirtualnej. Domyślnie rozmiar sterty to 1 MB. [Odwołanie EDITBIN](../../build/reference/editbin-reference.md) Zaokrągla liczbę w górę do najbliższej wielokrotności 4 bajty określona wartość.  
  
 Opcjonalny `commit` argument podlega interpretacji przez system operacyjny. W systemie operacyjnym Windows Określa początkowy ilość pamięci fizycznej do przydzielenia, a ilość więcej pamięci, aby przydzielić, gdy stos musi być rozwinięty. Zadeklarowanej pamięci wirtualnej spowoduje, że miejsca, które mają zostać zarezerwowane w pliku stronicowania. Wyższy `commit` wartość umożliwia systemowi można przydzielić pamięci mniej często w przypadku, gdy aplikacja potrzebuje więcej miejsca na stercie, ale zwiększa wymagania dotyczące pamięci i być może czas trwania uruchomienia aplikacji. `commit` Wartość musi być mniejsza lub równa `reserve` wartość.  
  
 Określ `reserve` i `commit` wartości dziesiętne lub notacji języka C szesnastkową lub ósemkowo. Na przykład wartość 1 MB można określić jako 1048576 dziesiątkowo, lub 0x100000 w formacie szesnastkowym lub 04000000 w ósemkowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje EDITBIN](../../build/reference/editbin-options.md)