---
title: Omówienie formantu edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 143fc93fb07d9ac7c4e803bbce426c114c02bfeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-the-rich-edit-control"></a>Omówienie formantu edycji wzbogaconej
> [!IMPORTANT]
>  Jeśli używasz kontrolki zaawansowanej edycji w oknie dialogowym (niezależnie od tego, czy aplikacja jest SDI i MDI, lub opartych na oknach dialogowych), należy wywołać [afxinitrichedit —](../mfc/reference/application-information-and-management.md#afxinitrichedit) po przed okno dialogowe jest wyświetlane okno. Typowe miejsce do wywołania tej funkcji znajduje się w programie pakietu `InitInstance` funkcję elementu członkowskiego. Nie trzeba wywołać ją za każdym razem, można wyświetlić okno dialogowe, tylko po raz pierwszy. Nie trzeba wywołać `AfxInitRichEdit` podczas pracy z `CRichEditView`.  
  
 Formanty edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) zapewnia interfejs programowania dla formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika należy udostępnić użytkownikowi operacji formatowania. Oznacza to zaawansowanej edycji formantu obsługuje zmienianie atrybutów znaków lub zaznaczonego tekstu. Przykłady znaku, który atrybuty pogrubienie, kursywa, rodziny czcionek i rozmiar w punktach. Przykładami akapitu atrybuty wyrównania, marginesami oraz właściwościami tabulatorów. Jednak jest maksymalnie o podanie interfejsu użytkownika, czy to przyciski paska narzędzi, elementy menu lub format znak okno dialogowe. Dostępne są również funkcje do badania kontrolki zaawansowanej edycji dla atrybutów bieżącego zaznaczenia. Korzystania z tych funkcji, aby wyświetlić bieżące ustawienia dla atrybutów, na przykład ustawienie znacznik wyboru w poleceniu interfejsu użytkownika, jeśli zaznaczenie zawiera znak bold atrybuty formatowania.  
  
 Aby uzyskać więcej informacji dotyczących formatowanie znaków i akapitów, zobacz [formatowanie znaków](../mfc/character-formatting-in-rich-edit-controls.md) i [formatowanie akapitów](../mfc/paragraph-formatting-in-rich-edit-controls.md) dalszej części tego tematu.  
  
 Edycji wzbogaconej obsługę formantów, prawie wszystkie operacje i komunikaty powiadomień używane z wielowierszowych formantów edycyjnych. Formanty edycji w związku z tym aplikacje, że już Użyj formantów edycji można można łatwo zmienić być sformatowany. Dodatkowe komunikaty i powiadomienia umożliwiają aplikacjom dostęp do formantów edycyjnych unikatowe dla zaawansowanych funkcji. Aby uzyskać informacje o formantach edycyjnych, zobacz [CEdit](../mfc/reference/cedit-class.md).  
  
 Aby uzyskać więcej informacji na powiadomień, zobacz [powiadomienia za pomocą formantu edycji wzbogaconej](../mfc/notifications-from-a-rich-edit-control.md) dalszej części tego tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

