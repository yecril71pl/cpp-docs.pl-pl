---
title: Wypełnianie pola listy z drugiego zbioru rekordów (MFC Data Access)
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
ms.openlocfilehash: 8664e98c6668568918cc0e6504a38119d2e71428
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336925"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Wypełnianie pola listy z drugiego zbioru rekordów (MFC Data Access)

Domyślnie widok rekordów jest skojarzony z pojedynczym obiektem zestawu rekordów, którego pola są mapowane do formantów widoku rekordów. Czasami można umieścić pole listy lub formant pola kombi w widoku rekordu i wypełnić go wartościami z drugiego obiektu zestawie rekordów. Użytkownik może użyć pola listy, aby wybrać nową kategorię informacji do wyświetlenia w widoku rekordu. W tym temacie wyjaśniono, jak i kiedy to zrobić.

> [!TIP]
> Należy pamiętać, że wypełnianie pola kombi lub pola listy ze źródła danych może być powolne. Podejmij środki ostrożności przed próbą wypełnienia formantu z zestawu rekordów dużą liczbą rekordów.

Model dla tego tematu składa się z podstawowego zestawie rekordów, który wypełnia formanty formularza, podczas gdy pomocniczy zestawie rekordów wypełnia pole listy lub pole kombi. Wybranie ciągu z pola listy powoduje, że program ponownie podsycił podstawowy zestawie rekordów na podstawie zaznaczonego. Poniższa procedura używa pola kombi, ale ma zastosowanie w równym stopniu do pola listy.

#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Aby wypełnić pole kombi lub pole listy z drugiego zestawie rekordów

1. Utwórz obiekt zestawu rekordów ([CRecordset](../mfc/reference/crecordset-class.md).

1. Uzyskaj wskaźnik do [obiektu CComboBox](../mfc/reference/ccombobox-class.md) dla kontrolki pola kombi.

1. Opróżnij pole kombi z poprzednią zawartością.

1. Przechodzenie między wszystkimi rekordami w komecie rekordów, wywołując [CComboBox::AddString](../mfc/reference/ccombobox-class.md#addstring) dla każdego ciągu z bieżącego rekordu, który chcesz dodać do pola kombi.

1. Zainicjować zaznaczenie w polu kombi.

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

Ta funkcja używa drugiego pliku `m_courseSet`recordset, który zawiera rekord dla `CComboBox` każdego `m_ctlCourseList`oferowanego kursu i formantu, który jest przechowywany w klasie widoku rekordu.

Funkcja pobiera `m_courseSet` z dokumentu i otwiera go. Następnie opróżnia `m_ctlCourseList` i przewija `m_courseSet`. Dla każdego rekordu funkcja wywołuje funkcję `AddString` elementu członkowskiego pola kombi, aby dodać wartość identyfikatora kursu z rekordu. Na koniec kod ustawia wybór pola kombi.

## <a name="see-also"></a>Zobacz też

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)
