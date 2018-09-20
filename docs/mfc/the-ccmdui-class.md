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
ms.openlocfilehash: 18b5675aff2d10f224238a1ba6d3b919e1b285a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374585"
---
# <a name="the-ccmdui-class"></a>Klasa CCmdUI

Gdy polecenie aktualizacji kieruje do jej obsługi, struktura przekazuje obsługi wskaźnik do `CCmdUI` obiektu (lub do obiektu `CCmdUI`-klasy pochodnej). Ten obiekt reprezentuje przycisk paska narzędzi lub elementu menu lub inny obiekt interfejsu użytkownika, który wygenerował polecenia. Procedura obsługi aktualizacji wywołuje element członkowski funkcji `CCmdUI` struktury za pomocą wskaźnika można zaktualizować obiektu interfejsu użytkownika. Na przykład poniżej przedstawiono procedury obsługi aktualizacji, wyczyść wszystkie elementu menu:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Ten program obsługi wywołania `Enable` funkcji składowej typu obiektu z dostępem do elementu menu. `Enable` udostępnia element do użycia.

## <a name="see-also"></a>Zobacz też

[Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

