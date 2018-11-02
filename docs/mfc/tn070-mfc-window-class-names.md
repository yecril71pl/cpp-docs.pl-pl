---
title: 'TN070: nazwy klas okien MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.classes
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: d59dc052cc253c8d036de0559018065e4ba7457d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533619"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: nazwy klas okien MFC

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

MFC windows, użyj nazwy klasy utworzony dynamicznie, która odzwierciedla funkcje okna. MFC generuje nazw klas dynamicznie okien ramowych, widoków i okna wyskakujące generowany przez aplikację. Okien dialogowych i formantów, generowane przez aplikację MFC mają nazwę klasy okna w danym dostarczonych przez Windows.

Możesz zastąpić nazwę klasy dynamicznie podana przez rejestrowanie klasy okna i korzystania z niego w zastąpieniu obiektu [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Nazwy klas dostarczonych przez MFC Dopasuj jeden z dwóch następujących form:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Cyfr szesnastkowych, które zastępują `%x` znaki są wypełniane dane z [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktury. MFC używa tej techniki, aby wiele klas C++ wymagające identyczne **WNDCLASS** struktury można udostępnić tej samej klasy okna zarejestrowane. W przeciwieństwie do większości prostych aplikacji Win32, aplikacji MFC mieć tylko jedną **WNDPROC**, dzięki czemu można łatwo udostępniać **WNDCLASS** struktur, aby oszczędzić czas i pamięci. Wymienne wartości `%x` znaków przedstawione powyżej są następujące:

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

Pierwszy formularz (`Afx:%x:%x`) jest używany podczas **hCursor**, **hbrBackground**, i **hIcon** wyświetlane są wszystkie **NULL**.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)<br/>
[TN020: konwencje nazewnictwa i numerowania identyfikatorów](../mfc/tn020-id-naming-and-numbering-conventions.md)

