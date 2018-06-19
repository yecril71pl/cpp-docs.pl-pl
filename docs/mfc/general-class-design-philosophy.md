---
title: Zasady ogólne projektowania klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b2d0915c4b2940e93b781e7a56e2640c64a7f20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344366"
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

