---
title: 'TN070: Nazwy klas okien MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.classes
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 8b06f7b3656284de18632185877fdbe382343f95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168040"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: Nazwy klas okien MFC

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

MFC windows, użyj nazwy klasy utworzony dynamicznie, która odzwierciedla funkcje okna. MFC generuje nazw klas dynamicznie okien ramowych, widoków i okna wyskakujące generowany przez aplikację. Okien dialogowych i formantów, generowane przez aplikację MFC mają nazwę klasy okna w danym dostarczonych przez Windows.

Możesz zastąpić nazwę klasy dynamicznie podana przez rejestrowanie klasy okna i korzystania z niego w zastąpieniu obiektu [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Nazwy klas dostarczonych przez MFC Dopasuj jeden z dwóch następujących form:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Cyfr szesnastkowych, które zastępują `%x` znaki są wypełniane dane z [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) struktury. MFC używa tej techniki, aby wiele klas C++ wymagające identyczne **WNDCLASS** struktury można udostępnić tej samej klasy okna zarejestrowane. W przeciwieństwie do większości prostych aplikacji Win32, aplikacji MFC mieć tylko jedną **WNDPROC**, dzięki czemu można łatwo udostępniać **WNDCLASS** struktur, aby oszczędzić czas i pamięci. Wymienne wartości `%x` znaków przedstawione powyżej są następujące:

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

Pierwszy formularz (`Afx:%x:%x`) jest używany podczas **hCursor**, **hbrBackground**, i **hIcon** wyświetlane są wszystkie **NULL**.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)<br/>
[TN020: Konwencje identyfikator nazewnictwa i numerowania](../mfc/tn020-id-naming-and-numbering-conventions.md)
