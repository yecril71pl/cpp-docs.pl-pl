---
title: 'TN070: Nazwy klas okien MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.classes
dev_langs:
- C++
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c66c434503bbd2c6d7ee1b0557fa73d843e0caaa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn070-mfc-window-class-names"></a>TN070: nazwy klas okien MFC
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 MFC windows Użyj nazwy klasy utworzony dynamicznie, która odzwierciedla funkcji okna. MFC generuje nazwy klas dynamicznie dla okien ramowych, widoków i okna podręczne produkowane przez aplikację. Okien dialogowych i formantów utworzonego przez MFC aplikacji ma nazwę klasy okna w dostarczonych z systemem Windows.  
  
 Można zastąpić nazwę klasy dynamicznie podana przez rejestrowanie klasy okna i używanie go na nadpisanie [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Nazwy klas MFC dostarczone mieści się jeden z dwóch następujących postaci:  
  
```  
Afx:%x:%x  
Afx:%x:%x:%x:%x:%x  
```  
  
 Cyfr szesnastkowych, które zastępują `%x` znaki są wypełnione z danych z [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury. Ta metoda używa MFC, aby wiele klas C++ wymagające identyczne **WNDCLASS** struktury można korzystać z tej samej klasy zarejestrowanych okna. W przeciwieństwie do większości prostych aplikacji Win32, aplikacji MFC mieć tylko jeden **WNDPROC**, więc można łatwo udostępniać **WNDCLASS** struktury tak, aby zaoszczędzić czas i pamięci. Wymienne wartości `%x` znaków pokazanym powyżej są następujące:  
  
- **WNDCLASS.hInstance**  
  
- **WNDCLASS.style**  
  
- **WNDCLASS.hCursor**  
  
- **WNDCLASS.hbrBackground**  
  
- **WNDCLASS.hIcon**  
  
 Pierwszy formularz (`Afx:%x:%x`) jest używany podczas **hCursor**, **hbrBackground**, i **hIcon** są wszystkie **NULL**.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)   
 [TN020: konwencje nazewnictwa i numerowania identyfikatorów](../mfc/tn020-id-naming-and-numbering-conventions.md)

