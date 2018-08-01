---
title: Koprocesor zmiennoprzecinkowy i Konwencje wywoływania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66ccd54c4abb1d8d9761d5ded88beba76bfae043
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401357"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor zmiennoprzecinkowy i konwencje wywoływania
Jeśli piszesz zestawu procedury dla zmiennoprzecinkowego punktu Koprocesor, należy zachować wartość zmiennoprzecinkowa punktem słowa sterującego i wyczyścić stosu Koprocesor, chyba że jest zwracany **float** lub **double** wartość (która funkcja powinna zwrócić w ST(0)).  
  
## <a name="see-also"></a>Zobacz także  
 [Konwencje wywoływania](../cpp/calling-conventions.md)