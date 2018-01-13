---
title: "Dodatkowe zagadnienia dotyczące uruchamiania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 57b1de8fbbdb3d969dca8e84e57e18b81749d944
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="additional-startup-considerations"></a>Dodatkowe zagadnienia dotyczące uruchamiania
W języku C++ konstrukcji obiektów i likwidacja może obejmować wykonywanie kodu użytkownika. W związku z tym należy zrozumieć, których inicjowanie stanie przed wejściem do **głównego** i destruktory, które są wywoływane po wyjściu z **głównego**. (Aby uzyskać szczegółowe informacje dotyczące konstruowania i niszczenie obiektów, zobacz [konstruktorów](../cpp/constructors-cpp.md) i [destruktory](../cpp/destructors-cpp.md).)  
  
 Inicjowanie następujące została wykonana przed wejściem do **głównego**:  
  
-   Domyślne inicjowanie danych statycznych od zera. Wszystkie dane statyczne bez jawnego inicjatory są ustawione na zero, przed wykonaniem innego kodu, w tym inicjowania środowiska wykonawczego. Statyczne elementy członkowskie danych nadal musi być jawnie zdefiniowany.  
  
-   Inicjowanie statyczne obiektów globalnych w jednostce tłumaczenia. To może wystąpić przed wejściem do **głównego** lub przed pierwszym użyciem dowolnej funkcji lub obiektu w jednostce tłumaczenia obiektu.  
  
 **Dotyczące firmy Microsoft**  
  
 W Microsoft C++ statycznych obiektów globalnych są inicjowane przed wejściem do **głównego**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Globalne obiekty statycznych, które są wykluczają się wzajemnie, ale w różnych tłumaczenia jednostki mogą spowodować nieprawidłowe zachowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie i kończenie działania](../cpp/startup-and-termination-cpp.md)