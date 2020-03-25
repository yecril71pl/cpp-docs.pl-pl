---
title: Wypełnianie pola listy z drugiego zestawu rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
ms.openlocfilehash: 8eb2525ef8b749f58303cae13b87b21d7df73d1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213411"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Wypełnianie pola listy z drugiego zestawu rekordów (dostęp do danych MFC)

Domyślnie widok rekordu jest skojarzony z pojedynczym obiektem zestawu rekordów, którego pola są mapowane na kontrolki widoku rekordu. Czasami warto umieścić formant pola listy lub pola kombi w widoku rekordu i wypełnić go wartościami z drugiego obiektu zestawu rekordów. Użytkownik może użyć pola listy, aby wybrać nową kategorię informacji, która ma być wyświetlana w widoku rekordu. W tym temacie wyjaśniono, jak i kiedy to zrobić.

> [!TIP]
>  Należy pamiętać, że wypełnienie pola kombi lub pola listy ze źródła danych może być powolne. Podejmuj środki ostrożności przed podjęciem próby wypełnienia formantu z zestawu rekordów o dużej liczbie rekordów.

Model tego tematu składa się z podstawowego zestawu rekordów, który wypełnia kontrolki formularza, podczas gdy pomocniczy zestaw rekordów wypełnia pole listy lub pole kombi. Wybranie ciągu z pola listy powoduje, że program będzie ponawiać kwerendę podstawowego zestawu rekordów na podstawie tego, co zostało wybrane. Poniższa procedura używa pola kombi, ale jest równie taka sama jak pole listy.

#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Aby wypełnić pole kombi lub pole listy z drugiego zestawu rekordów

1. Utwórz obiekt zestawu rekordów ([CRecordset](../mfc/reference/crecordset-class.md).

1. Uzyskaj wskaźnik do obiektu [CComboBox](../mfc/reference/ccombobox-class.md) dla kontrolki pole kombi.

1. Pole kombi pustej zawartości.

1. Przechodzenie przez wszystkie rekordy w zestawie rekordów, wywołując [CComboBox:: AddString](../mfc/reference/ccombobox-class.md#addstring) dla każdego ciągu z bieżącego rekordu, który ma zostać dodany do pola kombi.

1. Zainicjuj wybór w polu kombi.

```cpp
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

Ta funkcja używa drugiego zestawu rekordów `m_courseSet`, który zawiera rekord dla każdego oferowanego kursu, oraz kontrolkę `CComboBox`, `m_ctlCourseList`, która jest przechowywana w klasie widoku rekordów.

Funkcja pobiera `m_courseSet` z dokumentu i otwiera go. Następnie opróżnia `m_ctlCourseList` i przewija przez `m_courseSet`. Dla każdego rekordu funkcja wywołuje funkcję członkowską `AddString` pola kombi, aby dodać wartość identyfikatora kursu z rekordu. Na koniec kod ustawia zaznaczenie pola kombi.

## <a name="see-also"></a>Zobacz też

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)
