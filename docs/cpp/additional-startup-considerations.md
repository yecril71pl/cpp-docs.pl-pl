---
title: Dodatkowe zagadnienia dotyczące uruchamiania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c23f18a04010ba62d3651344464ff1668b2127d9
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405074"
---
# <a name="additional-startup-considerations"></a>Dodatkowe zagadnienia dotyczące uruchamiania
W języku C++ obiekt konstrukcje i zniszczenie ruchu może obejmować wykonywanie kodu użytkownika. Dlatego jest ważne, aby zrozumieć, które inicjalizacje się odbyć przed wpis, aby `main` i które destruktory są wywoływane po wyjściu z `main`. (Aby uzyskać szczegółowe informacje dotyczące budowa i niszczenie obiektów, zobacz [konstruktory](../cpp/constructors-cpp.md) i [destruktory](../cpp/destructors-cpp.md).)  
  
 Następujące inicjowanie odbywać się przed wejściem do `main`:  
  
-   Domyślna inicjalizacja danych statycznych do zera. Wszystkie dane statyczne, bez jawnego inicjatory są ustawiane na zero, przed wykonaniem wszelkich innych kodu, w tym inicjowania środowiska wykonawczego. Statyczne elementy członkowskie danych nadal muszą być jawnie zdefiniowane.  
  
-   Inicjowanie statycznych obiektów globalnych w jednostce translacji. Taka sytuacja może wystąpić przed wpis `main` lub przed pierwszym użyciem dowolnej funkcji lub obiektu w jednostce translacji obiektu.  
  
 **Microsoft Specific**  
  
 W Microsoft C++, obiekty globalne statyczne są inicjowane przed wejściem do `main`.  
  
 **END specyficzny dla Microsoft**  
  
 Statycznych obiektów globalnych, które są wzajemnie się wzajemnie, ale w jednostki translacji różnych mogą spowodować niepoprawne zachowanie.  
  
## <a name="see-also"></a>Zobacz także  
 [Uruchomienie i zakończenie](../cpp/startup-and-termination-cpp.md)