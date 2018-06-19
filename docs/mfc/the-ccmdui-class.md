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
ms.openlocfilehash: dde8c31620f64e6201c59b7031c789caa16c4902
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379811"
---
# <a name="the-ccmdui-class"></a>Klasa CCmdUI
Gdy polecenie aktualizacji kieruje do jego obsługi, platformę przekazuje program obsługi wskaźnik do `CCmdUI` obiektu (lub do obiektu `CCmdUI`-klasy). Ten obiekt reprezentuje przycisk menu element lub paska narzędzi lub innego obiektu interfejsu użytkownika, który wygenerował polecenia. Procedura obsługi aktualizacji wywołuje element członkowski funkcji `CCmdUI` struktury przez wskaźnik, aby zaktualizować obiekt interfejsu użytkownika. Na przykład w tym miejscu jest programu obsługi aktualizacji dla elementu menu Wyczyść wszystko:  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 Ten program obsługi wymaga **włączyć** funkcji członkowskiej klasy obiektu z dostępem do elementu menu. **Włącz** sprawia, że element jest dostępny do użycia.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

