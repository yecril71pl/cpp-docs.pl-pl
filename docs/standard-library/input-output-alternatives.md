---
title: Input-Output alternatyw | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4999aa9e7e1c5a2578f09bcaebb5e4a7fa934155
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="inputoutput-alternatives"></a>Input/Output Alternatives
Visual C++ oferuje różne możliwości użytkownikom programowania we/wy:  
  
-   C biblioteki wykonawczej bezpośrednie, Niebuforowane operacje We/Wy.  
  
-   We/Wy strumienia biblioteki wykonawczej języka C do ANSI.  
  
-   Konsoli i portu bezpośrednie we/wy.  
  
-   Biblioteka Microsoft Foundation Class.  
  
-   Biblioteka Microsoft C++ Standard.  
  
 Iostream, które klasy są przydatne w przypadku buforowane, sformatowanego tekstu we/wy. Są one również przydatne w przypadku operacji We/Wy Niebuforowane lub binary Jeśli należy interfejs programowania C++ i zrezygnować z biblioteki Microsoft Foundation Class (MFC). W klasach iostream są zamiast we/wy zorientowane obiektowo funkcje wykonawcze języka C.  
  
 Klasach iostream można użyć w systemie operacyjnym Microsoft Windows. Strumienie String i plik działa bez ograniczeń, ale obiektów strumienia tryb znakowy `cin`, `cout`, `cerr`, i `clog` są niezgodne z interfejsu graficznego użytkownika systemu Windows. Można również pochodzić klas niestandardowych strumieni, których bezpośrednią interakcję z środowiska systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Czym jest strumień?](../standard-library/what-a-stream-is.md)

