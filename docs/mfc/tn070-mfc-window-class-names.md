---
title: 'TN070: nazwy klas okien MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: ad43f5af5d2e90cb5fc2bc90f0909c2b495b4a4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373484"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: nazwy klas okien MFC

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

Okna MFC używają dynamicznie utworzonej nazwy klasy, która odzwierciedla operacje okna. MFC generuje nazwy klas dynamicznie dla okien ramek, widoków i okien podręcznych produkowanych przez aplikację. Okna dialogowe i formanty produkowane przez aplikację MFC mają nazwę dostarczoną przez system Windows dla danej klasy okna.

Można zastąpić dynamicznie podaną nazwę klasy, rejestrując własną klasę okna i używając jej w zastąpieniu [precreatewindow](../mfc/reference/cwnd-class.md#precreatewindow). Ich nazwy klas dostarczone przez MFC pasują do jednej z dwóch następujących form:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Cyfry szesnastkowe, które zastępują `%x` znaki, są wypełniane na podstawie danych ze struktury [WNDCLASS.](/windows/win32/api/winuser/ns-winuser-wndclassw) MFC używa tej techniki, dzięki czemu wiele klas Języka C++ wymagających identycznych struktur **WNDCLASS** może współużytkować tę samą klasę okna zarejestrowanych. W przeciwieństwie do większości prostych aplikacji Win32, aplikacje MFC mają tylko jeden **WNDPROC,** dzięki czemu można łatwo udostępniać struktury **WNDCLASS,** aby zaoszczędzić czas i pamięć. Wartości wymienne `%x` dla znaków pokazanych powyżej są następujące:

- **WNDCLASS.hInstance**

- **Styl WNDCLASS.style**

- **WNDCLASS.hKursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

Pierwsza forma`Afx:%x:%x`( ) jest używana, gdy **hCursor**, **hbrBackground**i **hIcon** są **null**.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)<br/>
[TN020: konwencje nazewnictwa i numerowania identyfikatorów](../mfc/tn020-id-naming-and-numbering-conventions.md)
