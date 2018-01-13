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
ms.workload: cplusplus
ms.openlocfilehash: 35e97e7bbbc04699e813b6890180512043c4e25d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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