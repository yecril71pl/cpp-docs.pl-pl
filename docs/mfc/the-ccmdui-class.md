---
title: Klasa CCmdUI
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 105aa7ad6c5cc6a5563dbde8145327a2b3d066a1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447141"
---
# <a name="the-ccmdui-class"></a>Klasa CCmdUI

Gdy kieruje polecenie Update do programu obsługi, struktura przekazuje programowi obsługi wskaźnik do obiektu `CCmdUI` (lub do obiektu klasy pochodnej `CCmdUI`). Ten obiekt reprezentuje element menu lub przycisk paska narzędzi lub inny obiekt interfejsu użytkownika, który wygenerował polecenie. Procedura obsługi aktualizacji wywołuje funkcje członkowskie struktury `CCmdUI` za pomocą wskaźnika, aby zaktualizować obiekt interfejsu użytkownika. Na przykład poniżej przedstawiono procedurę obsługi aktualizacji dla elementu menu Wyczyść wszystko:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Ta procedura obsługi wywołuje `Enable` funkcję członkowską obiektu z dostępem do elementu menu. `Enable` udostępnia element do użycia.

## <a name="see-also"></a>Zobacz też

[Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)
