---
title: "Wypełnianie pola listy z drugiego zestawu wierszy (dostęp do danych MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: de1282b80517a1c264121fbc0b749d3ca4ca2add
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Wypełnianie pola listy z drugiego zestawu wierszy (dostęp do danych MFC)
Domyślnie widoku rekordu jest skojarzony z obiektem pojedynczy zestaw rekordów, których pola są mapowane na formanty widoku rekordu. Czasami może chcesz umieścić pole listy lub pola kombi kontroli w widoku rekordów i uzupełnij go o wartości od drugiego obiektu zestawu rekordów. Użytkownik może użyć pola listy, aby wybrać nową kategorię informacje mają być wyświetlane w widoku rekordu. W tym temacie wyjaśniono, jak i kiedy w tym celu.  
  
> [!TIP]
>  Należy pamiętać, że wypełnianie pola kombi lub pola listy z źródła danych może być wolne. Zachować środki ostrożności przed próbą do wypełnienia kontrolki z zestawu rekordów z dużej liczby rekordów.  
  
 Model ten temat składa się z podstawowego zestawu rekordów, które wypełnia kontrolek formularza, gdy zestaw rekordów dodatkowej wypełnienia pola listy lub pola kombi. Zaznaczenie ciąg z pola listy powoduje, że programu requery podstawowy zestaw rekordów oparte na to, co zostało wybrane. Poniższa procedura używa pola kombi, ale informacje dotyczą pola listy.  
  
#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Aby wypełnić pole kombi lub pola listy z drugiego zestawu rekordów  
  
1.  Utwórz obiekt zestawu rekordów ([crecordset —](../mfc/reference/crecordset-class.md).  
  
2.  Wskaźnik do uzyskania [ccombobox —](../mfc/reference/ccombobox-class.md) obiektu dla kontrolki pola kombi.  
  
3.  Opróżnij wszystkie poprzednie zawartości pola kombi.  
  
4.  Przechodzenie między wszystkie rekordy w zestawie rekordów wywoływania [CComboBox::AddString](../mfc/reference/ccombobox-class.md#addstring) dla każdego ciągu z bieżącego rekordu, które chcesz dodać do pola kombi.  
  
5.  Inicjowanie zaznaczenie w polu kombi.  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
    // ...  
  
    // Fill the combo box with all of the courses  
    CENROLLDoc* pDoc = GetDocument();  
    if (!pDoc->m_courseSet.Open())  
        return;  
  
    // ...  
  
    m_ctlCourseList.ResetContent();  
    if (pDoc->m_courseSet.IsOpen())  
    {   
        while (!pDoc->m_courseSet.IsEOF() )  
        {  
            m_ctlCourseList.AddString(  
                pDoc->m_courseSet.m_CourseID);  
            pDoc->m_courseSet.MoveNext();  
        }  
    }  
    m_ctlCourseList.SetCurSel(0);  
}  
```  
  
 Ta funkcja korzysta z drugiego zestawu wierszy `m_courseSet`, który zawiera rekord dla każdego kursu oferowane, a `CComboBox` kontroli, `m_ctlCourseList`, który jest przechowywany w klasie widoku rekordu.  
  
 Pobiera funkcję `m_courseSet` z dokumentu i otwarcie go. A następnie go opróżnia `m_ctlCourseList` i przewija `m_courseSet`. Dla każdego rekordu, funkcja wywołuje pola kombi `AddString` funkcji członkowskiej, aby dodać wartość Identyfikatora ciągu z rekordu. Na koniec kod ustawia pole kombi pola wyboru.  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)   
 [Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)