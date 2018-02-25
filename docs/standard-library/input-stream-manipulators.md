---
title: "Manipulatory strumieni wejścia | Dokumentacja firmy Microsoft"
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
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e92b41ee4140ff08bd6578ef79a1d297734ba870
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="input-stream-manipulators"></a>Manipulatory strumieni wejścia
Wiele manipulatory, takich jak [setprecision](../standard-library/iomanip-functions.md#setprecision), są definiowane dla `ios` klasy i w związku z tym dotyczą strumienie. Kilka manipulatory, jednak faktycznie wpływa na obiekty strumienia wejściowego. Tych, które wykonują, najważniejsze są manipulatory radix `dec`, `oct`, i `hex`, określają podstawową konwersji używany z numerami ze strumienia wejściowego.  
  
 Na wyodrębniania `hex` manipulatora umożliwia przetwarzanie różnych formatów wejściowych. Na przykład c C, 0xc, 0xC 0Xc i 0XC będą interpretowane jako dziesiętna 12. Dowolny znak inny niż od 0 do 9, od A do F, do f x i X kończy konwersja liczbowa. W związku z tym sekwencji `"124n5"` jest konwertowana na numer 124 z [basic_ios::fail](../standard-library/basic-ios-class.md#fail) bitu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wejściowe](../standard-library/input-streams.md)

