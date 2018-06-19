---
title: Tworzenie niemodalnego arkusza właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10dbef813d922bd01a5f9215b6d6e642349d2b75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342725"
---
# <a name="creating-a-modeless-property-sheet"></a>Tworzenie niemodalnego arkusza właściwości
Zwykle będzie modalne arkuszy właściwości, które można utworzyć. Używając modalny arkusz właściwości, użytkownik musi zamknąć arkusz właściwości przed rozpoczęciem korzystania z innych części aplikacji. W tym artykule opisano metody, które umożliwia tworzenie niemodalnego arkusza właściwości przez użytkownika pozostawić arkusz właściwości otwarte podczas korzystania z innych części aplikacji.  
  
 Aby wyświetlić arkusz właściwości jako niemodalnego okna dialogowego zamiast jako modalne okno dialogowe, wywołaj [CPropertySheet::Create](../mfc/reference/cpropertysheet-class.md#create) zamiast [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). Musi implementować też kilka dodatkowych zadań, aby obsługiwać niemodalnego arkusza właściwości.  
  
 Jest jednym z dodatkowych zadań wymiany danych między arkusz właściwości i obiektu zewnętrznego, który modyfikuje po otwarciu arkusza właściwości. Zwykle jest to samo zadanie, podobnie jak w przypadku standardowego Niemodalne okna dialogowe. Część to zadanie implementuje kanał komunikacji między niemodalnego arkusza właściwości i zewnętrznego obiektu, do którego odnoszą się ustawienia właściwości. Ta implementacja jest znacznie łatwiejsze, jeśli pochodzi z klasy [cpropertysheet —](../mfc/reference/cpropertysheet-class.md) dla Twojego niemodalnego arkusza właściwości. W tym artykule przyjęto założenie, że zostało to zrobione.  
  
 Jedną z metod komunikacji między niemodalnego arkusza właściwości i zewnętrznej obiektu (bieżące zaznaczenie w widoku, na przykład) jest określenie wskaźnika z arkusza właściwości do obiektu zewnętrznego. Zdefiniuj funkcję (nazywane wyglądać mniej więcej tak `SetMyExternalObject`) w `CPropertySheet`-klasy, aby zmienić wskaźnik przy każdej zmianie fokusu z jednego obiektu zewnętrznego do innego. `SetMyExternalObject` Funkcja konieczne zresetowanie ustawień dla każdej strony właściwości, aby odzwierciedlić nowo wybranego obiektu zewnętrznego. Aby to osiągnąć, `SetMyExternalObject` funkcja musi być w stanie uzyskać dostępu do [cpropertypage —](../mfc/reference/cpropertypage-class.md) obiektów należących do `CPropertySheet` klasy.  
  
 Najbardziej wygodny sposób w celu zapewnienia dostępu do strony właściwości w arkuszu właściwości jest osadzenie `CPropertyPage` obiekty w `CPropertySheet`-pochodzi z obiektu. Osadzanie `CPropertyPage` obiekty w `CPropertySheet`-obiektu pochodnego różni się od typowego projektu dla modalne okna dialogowe, gdy właściciel arkusza właściwości tworzy `CPropertyPage` obiekty i przekazuje je do arkusza właściwości, za pomocą [ CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage).  
  
 Istnieje wiele alternatyw interfejsu użytkownika, określając stosowania ustawień niemodalnego arkusza właściwości do obiektu zewnętrznego. Jeden alternatywą jest do zastosowania ustawień bieżącej strony właściwości zawsze, gdy użytkownik zmieni się dowolna wartość. Alternatywą jest zapewnienie przycisk Zastosuj, który umożliwia użytkownikowi accumulate zmiany na stronach właściwości przed zatwierdzeniem je do obiektu zewnętrznego. Aby uzyskać informacje dotyczące sposobów obsługi przycisk Zastosuj, zobacz artykuł [Obsługa przycisku Zastosuj](../mfc/handling-the-apply-button.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)   
 [Wymiana danych](../mfc/exchanging-data.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

