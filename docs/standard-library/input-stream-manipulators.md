---
title: Manipulatory strumieni wejścia
ms.date: 11/04/2016
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
ms.openlocfilehash: 17f18aa127b84538229b3cf4e4246dfefb6c1f98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404913"
---
# <a name="input-stream-manipulators"></a>Manipulatory strumieni wejścia

Manipulatory wiele takich jak [setprecision](../standard-library/iomanip-functions.md#setprecision), są zdefiniowane dla `ios` klasy i w związku z tym dotyczą strumienie wejściowe. Manipulatory kilka jednak faktycznie wpływa na obiekty strumienia wejściowego. Takie, które są najważniejsze są manipulatory podstawy, `dec`, `oct`, i `hex`, które określają podstawowy konwersji używane z międzynarodowymi numerami identyfikującymi ze strumienia wejściowego.

Na wyodrębniania `hex` manipulator umożliwia przetwarzanie różnych formatów danych wejściowych. Na przykład c C, 0xc, 0xC, 0Xc i 0XC są interpretowane jako dziesiętna liczba całkowita 12. Dowolny znak inny niż od 0 do 9, od A do F, do f x i X kończy konwersji numerycznej. Ten sposób sekwencji `"124n5"` jest konwertowany na liczbę 124 [basic_ios::fail](../standard-library/basic-ios-class.md#fail) bitu.

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
