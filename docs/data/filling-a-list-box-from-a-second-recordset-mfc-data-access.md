---
title: Wypełnianie pola listy z drugiego zestawu rekordów (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c5261a6bacb9fc0bf580820073699cc442218db
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072750"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Wypełnianie pola listy z drugiego zestawu rekordów (dostęp do danych MFC)

Domyślnie w widokiem rekordu jest skojarzony z obiektem pojedynczy zestaw rekordów, których pola są zamapowane na kontrolkę widoku rekordu. Czasami możesz chcieć umieścić pola listy lub pola kombi kontrolować w widoku rekordu i wypełnić ją przy użyciu wartości z obiektu drugiego zestawu rekordów. Użytkownika można użyć pola listy, aby wybrać nową kategorię informacje mają być wyświetlane w widoku rekordu. W tym temacie wyjaśniono, jak i kiedy to zrobić.

> [!TIP]
>  Należy pamiętać, że wypełnianie pola kombi lub pola listy z źródła danych może być wolne. Podjąć środki ostrożności przeciwko do wypełniania kontrolki z poziomu zestawu rekordów z dużą liczbę rekordów.

Model, w tym temacie składa się z podstawowego zestawu rekordów, które wypełnia kontrolek formularza, podczas gdy pomocniczego zestawu rekordów wypełnienia pola listy lub pola kombi. Wybierając ciąg w polu listy powoduje, że program requery podstawowy zestaw rekordów, co zostało wybrane w oparciu. Poniższa procedura korzysta z pola kombi, ale stosuje się jednakowo do pola listy.

#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Aby wypełnić pola kombi lub pola listy z drugiego zestawu rekordów

1. Utwórz obiekt zestawu rekordów ([CRecordset](../mfc/reference/crecordset-class.md).

1. Uzyskiwanie wskaźnika do [CComboBox](../mfc/reference/ccombobox-class.md) obiekt do kontrolki pola kombi.

1. Puste pola kombi, wszystkie poprzednie treści.

1. Przechodzenie między wszystkie rekordy w zestawie rekordów wywoływania [CComboBox::AddString](../mfc/reference/ccombobox-class.md#addstring) dla każdego ciągu z bieżącego rekordu, który chcesz dodać do pola kombi.

1. Inicjuj zaznaczenie w polu kombi.

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

Ta funkcja korzysta z drugiego zestawu rekordów `m_courseSet`, która zawiera rekord dla każdego kursu oferowane i `CComboBox` kontroli `m_ctlCourseList`, który jest przechowywany w klasie widoku rekordu.

Funkcja pobiera `m_courseSet` z dokumentu i otwiera go. A następnie opróżnia je `m_ctlCourseList` i przewija `m_courseSet`. Dla każdego rekordu, funkcja wywołuje pola kombi `AddString` funkcja elementu członkowskiego, aby dodać wartości Identyfikatora kurs z rekordu. Na koniec kod ustawia kombi pola wyboru.

## <a name="see-also"></a>Zobacz też

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)