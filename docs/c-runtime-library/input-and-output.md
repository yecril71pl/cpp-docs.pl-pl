---
title: "Wejście i wyjście | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5c4705ae56f11c1299e512814f8d83a49690a6ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="input-and-output"></a>Dane wejściowe i wyjściowe
Funkcje We/Wy odczytu i zapisu danych do i z plików i urządzeń. Operacje We/Wy pliku została wykonana w trybie tekst lub binarny. Biblioteka wykonawcza Microsoft zawiera trzy funkcje We/Wy:  
  
-   [We/Wy strumienia](../c-runtime-library/stream-i-o.md) funkcje traktować danych jako strumień znaki.  
  
-   [We/Wy niskiego poziomu](../c-runtime-library/low-level-i-o.md) systemu operacyjnego bezpośrednio dla operacji niższe niż te dostarczone przez we/wy strumienia wywołania funkcji.  
  
-   [Konsoli i portu We/Wy](../c-runtime-library/console-and-port-i-o.md) funkcji odczytu lub zapisu bezpośrednio w konsoli (klawiatury i ekranu), czy port We/Wy (na przykład port drukarki).  
  
    > [!NOTE]
    >  Ponieważ funkcje strumienia są buforowane, a nie są funkcje niskiego poziomu, te dwa typy funkcji są zazwyczaj niezgodne. Dla przetwarzania danego pliku, użyj wyłącznie strumienia lub funkcje niskiego poziomu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)