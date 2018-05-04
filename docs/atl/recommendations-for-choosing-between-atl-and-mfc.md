---
title: Zalecenia dotyczące wybierania pomiędzy ATL i MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116f2066b98951aa2a470021f5527542ac8cbe46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Zalecenia dotyczące wybierania pomiędzy ATL i MFC
Podczas tworzenia składników i aplikacji, można wybrać dwa podejścia — ATL i MFC (Microsoft Foundation Class Library).  
  
## <a name="using-atl"></a>Za pomocą biblioteki ATL  
 ATL jest szybki i łatwy sposób zarówno tworzenie składnika modelu COM w języku C++ i obsługa niewielkie rozmiary. ATL umożliwia tworzenie formantu, jeśli nie potrzebujesz wszystkich funkcji wbudowanych automatycznie zapewniająca MFC.  
  
## <a name="using-mfc"></a>Za pomocą MFC  
 MFC służy do tworzenia aplikacji pełne, formantów ActiveX i dokumenty aktywne. Jeśli utworzono już formantu z MFC, można kontynuować programowanie w MFC. Tworząc nową kontrolkę, należy rozważyć użycie ATL, jeśli nie potrzebujesz wszystkich funkcji wbudowanych MFC.  
  
## <a name="using-atl-in-an-mfc-project"></a>Za pomocą biblioteki ATL w projekcie MFC  
 Możesz dodać obsługę za pomocą biblioteki ATL w projekcie MFC istniejących za pomocą kreatora. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi ATL do projektu MFC Your](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do ATL](../atl/introduction-to-atl.md)

