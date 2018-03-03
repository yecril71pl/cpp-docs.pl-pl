---
title: "Zasady ogólne projektowania klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c174b06b27e78ca61d2608b8e04205068ac436e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="general-class-design-philosophy"></a>Ogólne zasady projektowania klas
Microsoft Windows zostało zaprojektowane na długo przed popularnych aktywowano języka C++. Ponieważ tysiące aplikacje korzystają z interfejsu programowania aplikacji (API) języka C z systemem Windows, ten interfejs będzie przechowywany w najbliższej przyszłości. Każdy interfejs Windows w języku C++ w związku z tym muszą być zbudowane w oparciu procedur API języka C. Gwarantuje to, że aplikacji C++ będą mogli współistnieć z aplikacji C.  
  
 Microsoft Foundation Class Library jest zorientowany obiektowo interfejs do systemu Windows, która spełnia następujące cele projektowania:  
  
-   Znaczny spadek starań, aby tworzyć aplikacje dla systemu Windows.  
  
-   Szybkość wykonywania jest porównywalna do interfejsu API języka C.  
  
-   Kod minimalny rozmiar koszty.  
  
-   Możliwość wywołania dowolnej funkcji Windows C bezpośrednio.  
  
-   Łatwiejsze konwersji istniejących aplikacji C języka c++.  
  
-   Możliwość korzystania z istniejącej bazy systemu Windows języka C środowiska programowania.  
  
-   Łatwiejsze korzystanie z interfejsu API systemu Windows w języku C++ niż z C.  
  
-   Łatwiejsze do wykorzystania jeszcze zaawansowanych abstrakcje skomplikowane funkcje, takie jak kontrolki ActiveX, obsługa baz danych, drukowania, paski narzędzi i paski stanu.  
  
-   Wartość true, interfejsu API systemu Windows dla języka C++, które skutecznie wykorzystuje funkcje języka C++.  
  
 Aby uzyskać więcej informacji na temat projektu biblioteki MFC zobacz:  
  
-   [Struktura aplikacji](../mfc/application-framework.md)  
  
-   [Relacja z interfejsem API języka C](../mfc/relationship-to-the-c-language-api.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

