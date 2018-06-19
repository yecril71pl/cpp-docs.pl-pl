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
ms.openlocfilehash: c05ce0fa1a80de8f5ab8b9335bbab22628f3f158
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409725"
---
# <a name="additional-startup-considerations"></a>Dodatkowe zagadnienia dotyczące uruchamiania
W języku C++ konstrukcji obiektów i likwidacja może obejmować wykonywanie kodu użytkownika. W związku z tym należy zrozumieć, których inicjowanie stanie przed wejściem do **głównego** i destruktory, które są wywoływane po wyjściu z **głównego**. (Aby uzyskać szczegółowe informacje dotyczące konstruowania i niszczenie obiektów, zobacz [konstruktorów](../cpp/constructors-cpp.md) i [destruktory](../cpp/destructors-cpp.md).)  
  
 Inicjowanie następujące została wykonana przed wejściem do **głównego**:  
  
-   Domyślne inicjowanie danych statycznych od zera. Wszystkie dane statyczne bez jawnego inicjatory są ustawione na zero, przed wykonaniem innego kodu, w tym inicjowania środowiska wykonawczego. Statyczne elementy członkowskie danych nadal musi być jawnie zdefiniowany.  
  
-   Inicjowanie statyczne obiektów globalnych w jednostce tłumaczenia. To może wystąpić przed wejściem do **głównego** lub przed pierwszym użyciem dowolnej funkcji lub obiektu w jednostce tłumaczenia obiektu.  
  
 **Microsoft Specific**  
  
 W Microsoft C++ statycznych obiektów globalnych są inicjowane przed wejściem do **głównego**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Globalne obiekty statycznych, które są wykluczają się wzajemnie, ale w różnych tłumaczenia jednostki mogą spowodować nieprawidłowe zachowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchomienie i zakończenie](../cpp/startup-and-termination-cpp.md)