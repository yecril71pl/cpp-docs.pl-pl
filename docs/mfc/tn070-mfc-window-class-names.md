---
title: 'TN070: Nazwy klas okien MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 1d9b5de07bcc2545df6294557d1ac9f9d29e856c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513355"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: Nazwy klas okien MFC

> [!NOTE]
>  Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

Windows MFC używa dynamicznie utworzonej nazwy klasy, która odzwierciedla funkcje okna. MFC generuje nazwy klas dynamicznie dla okien ramowych, widoków i okien podręcznych tworzonych przez aplikację. Okna dialogowe i kontrolki tworzone przez aplikację MFC mają nazwę dostarczoną przez system Windows dla danej klasy okna.

Można zastąpić dynamiczną nazwę klasy przez zarejestrowanie własnej klasy okna i użycie jej w przesłonięciu [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Nazwy klas dostarczone przez MFC pasują do jednej z dwóch następujących form:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Cyfry szesnastkowe, które zastępują `%x` znaki, są wypełniane danymi ze struktury [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) . MFC korzysta z tej techniki, dzięki C++ czemu wiele klas wymagających identycznych struktur **WNDCLASS** może współużytkować tę samą zarejestrowanej klasy okna. W przeciwieństwie do większości prostych aplikacji Win32, aplikacje MFC mają tylko jeden **WndProc**, więc można łatwo udostępniać struktury **WNDCLASS** , aby zaoszczędzić czas i pamięć. Wartości do przemieszczenia dla `%x` przedstawionych powyżej znaków są następujące:

- **WNDCLASS. hInstance**

- **WNDCLASS. Style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

Pierwszy`Afx:%x:%x`formularz () jest używany, gdy **hCursor**, **hbrBackground**i **HICON** mają **wartość null**.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)<br/>
[TN020: konwencje nazewnictwa i numerowania identyfikatorów](../mfc/tn020-id-naming-and-numbering-conventions.md)
