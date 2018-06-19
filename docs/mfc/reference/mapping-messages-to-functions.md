---
title: Mapowanie komunikatów na funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3388cd8e9a52ef9aacb427d66b027d793b08ca75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371637"
---
# <a name="mapping-messages-to-functions"></a>Mapowanie komunikatów na funkcje
Okno właściwości umożliwia powiązanie obsługi komunikatów (funkcje Członkowskie klas MFC interfejsu użytkownika) na komunikaty generowane przez zasobów aplikacji. Używają [mapy wiadomości MFC](../../mfc/messages-and-commands-in-the-framework.md) można utworzyć powiązania.  
  
 Podczas tworzenia nowej klasy pochodzącej od jednej z klas framework za pomocą widoku klasy, on automatycznie miejsca, a pełne i funkcjonalności klasy w plikach nagłówków (.h) i implementacji (.cpp) plików, które określisz.  
  
> [!NOTE]
>  Aby dodać nowe klasy, która nie zapewnia obsługi wiadomości, należy utworzyć klasę bezpośrednio w edytorze tekstu.  
  
### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>Aby zdefiniować lub usuń program obsługi komunikatów w oknie właściwości  
  
1.  W widoku klas kliknij klasy.  
  
2.  Kliknij w oknie właściwości **wiadomości** przycisku.  
  
    > [!NOTE]
    >  **Wiadomości** przycisk jest dostępny po wybraniu nazwy klasy w widoku klas lub po kliknięciu w oknie źródła.  
  
     Jeśli projekt zawiera obsługi wiadomości, nazwę programu obsługi jest wyświetlany w prawej kolumnie obok komunikatu.  
  
3.  Jeśli wiadomość ma bez obsługi, należy kliknąć komórki w prawej kolumnie w oknie właściwości, aby wyświetlić sugerowane nazwę programu obsługi jako \<Dodaj >*HandlerName*. (Na przykład `WM_TIMER` sugeruje obsługi wiadomości \<Dodaj >`OnTimer`).  
  
4.  Kliknij, aby dodać kod klasy zastępczej dla funkcji.  
  
5.  Aby edytować obsługi wiadomości, kliknij dwukrotnie komunikat w widoku klas i edytować kod w oknie źródła.  
  
 Aby usunąć program obsługi komunikatów, kliknij dwukrotnie program obsługi w prawej kolumnie, a następnie wybierz \<usunąć >*HandlerName*. Kod funkcji jest oznaczone jako komentarz.  
  
## <a name="see-also"></a>Zobacz też  
 [Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Dodawanie programów obsługi zdarzeń dla formantów okna dialogowego](../../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
