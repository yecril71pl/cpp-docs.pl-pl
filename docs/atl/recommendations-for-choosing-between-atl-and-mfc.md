---
title: "Zalecenia dotyczące wybierania pomiędzy ATL i MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d912c6cd997c23b9623d20a104327fb6e4701494
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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

