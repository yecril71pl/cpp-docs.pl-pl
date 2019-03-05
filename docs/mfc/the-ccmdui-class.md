---
title: Klasa CCmdUI
ms.date: 11/04/2016
f1_keywords:
- CCmdUI
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 8e0af0703924d6fae626d3753b8523efe0c56652
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326631"
---
# <a name="the-ccmdui-class"></a>Klasa CCmdUI

Gdy polecenie aktualizacji kieruje do jej obsługi, struktura przekazuje obsługi wskaźnik do `CCmdUI` obiektu (lub do obiektu `CCmdUI`-klasy pochodnej). Ten obiekt reprezentuje przycisk paska narzędzi lub elementu menu lub inny obiekt interfejsu użytkownika, który wygenerował polecenia. Procedura obsługi aktualizacji wywołuje element członkowski funkcji `CCmdUI` struktury za pomocą wskaźnika można zaktualizować obiektu interfejsu użytkownika. Na przykład poniżej przedstawiono procedury obsługi aktualizacji, wyczyść wszystkie elementu menu:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Ten program obsługi wywołania `Enable` funkcji składowej typu obiektu z dostępem do elementu menu. `Enable` udostępnia element do użycia.

## <a name="see-also"></a>Zobacz także

[Instrukcje: Aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)
