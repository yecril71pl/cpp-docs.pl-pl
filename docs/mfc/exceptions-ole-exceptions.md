---
title: "Wyjątki: Wyjątki OLE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67be1947b3fa08c26d659838922ce42a905167a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-ole-exceptions"></a>Wyjątki: wyjątki OLE
Techniki i urządzenia do obsługi wyjątków w OLE są takie same jak do obsługi innych wyjątków. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz artykuł [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md).  
  
 Wszystkie obiekty wyjątków są uzyskiwane z abstrakcyjna klasa podstawowa `CException`. Obsługa wyjątków OLE MFC zawiera dwie klasy:  
  
-   [COleException](../mfc/reference/coleexception-class.md) obsługi ogólne wyjątki OLE.  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) do generowania i obsługa OLE wysyłania wyjątków (automatyzacji).  
  
 Różnica między te dwie klasy jest ilość informacji stanowią i gdzie są używane. `COleException`ma element członkowski danych publicznych, który zawiera kod stanu OLE dla wyjątku. `COleDispatchException`dostarcza więcej informacji, takie jak następujące:  
  
-   Kod błędu specyficzne dla aplikacji  
  
-   Opis błędu, takie jak "Zapełniony dysk"  
  
-   Kontekst pomocy używaną przez aplikację do znajdują się dodatkowe informacje dla użytkownika  
  
-   Nazwa pliku pomocy aplikacji  
  
-   Nazwa aplikacji, która wygenerowała wyjątek  
  
 `COleDispatchException`zawiera więcej informacji, dzięki czemu można z produktami, takich jak Microsoft Visual Basic. Opis błędu ustne mogą być używane w oknie komunikatu lub innych powiadomień; informacje pomocy można pomóc użytkownikowi w odpowiedzi na warunki, które spowodowało wyjątek.  
  
 Dwie funkcje globalne odpowiadają dwie klasy wyjątków OLE: [afxthrowoleexception —](../mfc/reference/exception-processing.md#afxthrowoleexception) i [afxthrowoledispatchexception —](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Służą one do throw ogólne wyjątki OLE i wyjątki wysyłania OLE, odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

