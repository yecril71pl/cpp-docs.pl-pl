---
title: Manipulatory strumieni wejścia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30f642dc4942491bd73265e3d647d3281f97c1e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="input-stream-manipulators"></a>Manipulatory strumieni wejścia

Wiele manipulatory, takich jak [setprecision](../standard-library/iomanip-functions.md#setprecision), są definiowane dla `ios` klasy i w związku z tym dotyczą strumienie. Kilka manipulatory, jednak faktycznie wpływa na obiekty strumienia wejściowego. Tych, które wykonują, najważniejsze są manipulatory radix `dec`, `oct`, i `hex`, określają podstawową konwersji używany z numerami ze strumienia wejściowego.

Na wyodrębniania `hex` manipulatora umożliwia przetwarzanie różnych formatów wejściowych. Na przykład c C, 0xc, 0xC 0Xc i 0XC będą interpretowane jako dziesiętna 12. Dowolny znak inny niż od 0 do 9, od A do F, do f x i X kończy konwersja liczbowa. W związku z tym sekwencji `"124n5"` jest konwertowana na numer 124 z [basic_ios::fail](../standard-library/basic-ios-class.md#fail) bitu.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
