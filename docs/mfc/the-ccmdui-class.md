---
title: Klasa CCmdUI | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CCmdUI
dev_langs: C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 76f5dd1fa4ebaaa3a8c53f9eb27d6c83efd81bfd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="the-ccmdui-class"></a>Klasa CCmdUI
Gdy polecenie aktualizacji kieruje do jego obsługi, platformę przekazuje program obsługi wskaźnik do `CCmdUI` obiektu (lub do obiektu `CCmdUI`-klasy). Ten obiekt reprezentuje przycisk menu element lub paska narzędzi lub innego obiektu interfejsu użytkownika, który wygenerował polecenia. Procedura obsługi aktualizacji wywołuje element członkowski funkcji `CCmdUI` struktury przez wskaźnik, aby zaktualizować obiekt interfejsu użytkownika. Na przykład w tym miejscu jest programu obsługi aktualizacji dla elementu menu Wyczyść wszystko:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 Ten program obsługi wymaga **włączyć** funkcji członkowskiej klasy obiektu z dostępem do elementu menu. **Włącz** sprawia, że element jest dostępny do użycia.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

