---
title: Klasa CCmdUI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CCmdUI
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a857d1cddcc78c7cfff4243b9c99194986af3d9b
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956489"
---
# <a name="the-ccmdui-class"></a>Klasa CCmdUI
Gdy polecenie aktualizacji kieruje do jego obsługi, platformę przekazuje program obsługi wskaźnik do `CCmdUI` obiektu (lub do obiektu `CCmdUI`-klasy). Ten obiekt reprezentuje przycisk menu element lub paska narzędzi lub innego obiektu interfejsu użytkownika, który wygenerował polecenia. Procedura obsługi aktualizacji wywołuje element członkowski funkcji `CCmdUI` struktury przez wskaźnik, aby zaktualizować obiekt interfejsu użytkownika. Na przykład w tym miejscu jest programu obsługi aktualizacji dla elementu menu Wyczyść wszystko:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 Ten program obsługi wymaga `Enable` funkcji członkowskiej klasy obiektu z dostępem do elementu menu. `Enable` udostępnia element do użycia.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

