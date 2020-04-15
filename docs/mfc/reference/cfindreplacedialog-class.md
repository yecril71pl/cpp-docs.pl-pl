---
title: Klasa CFindReplaceDialog
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 7a12d0520d070d74afd9fa91e828970d14c82700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373861"
---
# <a name="cfindreplacedialog-class"></a>Klasa CFindReplaceDialog

Umożliwia implementowanie standardowych okien dialogowych znajdowania/zamieniania ciągu w aplikacji.

## <a name="syntax"></a>Składnia

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Wywołanie tej funkcji, aby skonstruować `CFindReplaceDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFindReplaceDialog::Utwórz](#create)|Tworzy i `CFindReplaceDialog` wyświetla okno dialogowe.|
|[CFindReplaceDialog::FindNext](#findnext)|Wywołanie tej funkcji, aby ustalić, czy użytkownik chce znaleźć następne wystąpienie ciąg find.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Wywołanie tej funkcji, aby pobrać bieżący ciąg find.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Wywołanie tej funkcji, `FINDREPLACE` aby pobrać strukturę w programie obsługi wiadomości zarejestrowanych.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Wywołanie tej funkcji, aby pobrać bieżący ciąg wymiany.|
|[CFindReplaceDialog::IsTerminating](#isterminating)|Wywołanie tej funkcji, aby ustalić, czy okno dialogowe jest zakończone.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Wywołanie tej funkcji, aby ustalić, czy użytkownik chce dokładnie dopasować przypadek find string.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Wywołanie tej funkcji, aby ustalić, czy użytkownik chce dopasować tylko całe słowa.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Wywołanie tej funkcji, aby ustalić, czy użytkownik chce wszystkie wystąpienia ciągu do zastąpienia.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Wywołanie tej funkcji, aby ustalić, czy użytkownik chce bieżącego wyrazu do zastąpienia.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Wywołanie tej funkcji, aby ustalić, czy użytkownik chce, aby wyszukiwanie kontynuować w kierunku w dół.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Struktura używana do dostosowywania `CFindReplaceDialog` obiektu.|

## <a name="remarks"></a>Uwagi

W przeciwieństwie do innych `CFindReplaceDialog` typowych okien dialogowych systemu Windows obiekty są niemodalne, umożliwiając użytkownikom interakcję z innymi oknami, gdy znajdują się na ekranie. Istnieją dwa rodzaje `CFindReplaceDialog` obiektów: Znajdowanie okien dialogowych oraz okna dialogowe Znajdowanie/zamienianie. Mimo że okna dialogowe umożliwiają użytkownikowi wprowadzanie ciągów wyszukiwania i wyszukiwania/zastępowania, nie wykonują one żadnej z funkcji wyszukiwania lub zastępowania. Należy dodać je do aplikacji.

Aby skonstruować `CFindReplaceDialog` obiekt, należy użyć dostarczonego konstruktora (który nie ma argumentów). Ponieważ jest to niemodless okna dialogowego, przydzielić obiekt na stercie przy użyciu **nowego** operatora, a nie na stosie.

Po `CFindReplaceDialog` zbudowaniu obiektu należy wywołać funkcję [Utwórz](#create) element członkowski, aby utworzyć i wyświetlić okno dialogowe.

Za pomocą [struktury m_fr](#m_fr) należy zainicjować okno `Create`dialogowe przed wywołaniem . Struktura `m_fr` jest typu [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

Aby okno nadrzędne było powiadamiane o żądaniach znajdowania/zamieniania, należy użyć funkcji [Windows RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) i użyć [makra ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) mapy wiadomości w oknie ramki obsługującego tę zarejestrowaną wiadomość.

Można określić, czy użytkownik zdecydował się zakończyć `IsTerminating` okno dialogowe za pomocą funkcji elementu członkowskiego.

`CFindReplaceDialog`opiera się na COMMDLG. DLL, który jest dostarczany z systemem Windows w wersji 3.1 lub nowszej.

Aby dostosować okno dialogowe, wydziel klasę z `CFindReplaceDialog`programu , podaj niestandardowy szablon okna dialogowego i dodaj mapę wiadomości, aby przetworzyć wiadomości powiadomień z rozszerzonych formantów. Wszelkie nieprzetworzene wiadomości powinny być przekazywane do klasy podstawowej.

Dostosowywanie funkcji haka nie jest wymagane.

Aby uzyskać więcej `CFindReplaceDialog`informacji na temat używania programu , zobacz [Typowe klasy dialogów dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CKlogialny](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog

Konstruuje `CFindReplaceDialog` obiekt.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Uwagi

Ponieważ `CFindReplaceDialog` obiekt jest niemodytowym okno dialogowe, należy skonstruować go na stercie przy użyciu **nowego** operatora.

Podczas niszczenia, ramach próbuje wykonać **usunąć to** na wskaźnik do okna dialogowego. Jeśli utworzono okno dialogowe na stosie, **ten** wskaźnik nie istnieje i może spowodować niezdefiniowane zachowanie.

Aby uzyskać więcej informacji `CFindReplaceDialog` na temat budowy obiektów, zobacz [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) omówienie. Użyj [funkcji CFindReplaceDialog::Utwórz](#create) element członkowski, aby wyświetlić okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFindReplaceDialog::Utwórz

Tworzy i wyświetla obiekt okna dialogowego Znajdowanie lub Znajdowanie/Zamienianie, w zależności od wartości pliku `bFindDialogOnly`.

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bZnajdowaniedialogOnly*<br/>
Ustaw ten parametr na WARTOŚĆ TRUE, aby wyświetlić okno dialogowe **Znajdowanie.** Ustaw wartość FAŁSZ, aby wyświetlić okno dialogowe **Znajdowanie/zamienianie.**

*lpszFindCo*<br/>
Wskaźnik do domyślnego ciągu wyszukiwania po wyświetleniu okna dialogowego. Jeśli null, okno dialogowe nie zawiera domyślnego ciągu wyszukiwania.

*lpszReplaceWith*<br/>
Wskaźnik do domyślnego ciągu zastępczego po wyświetleniu okna dialogowego. Jeśli null, okno dialogowe nie zawiera domyślnego ciągu zastępczego.

*Dwflags*<br/>
Co najmniej jedna flaga służy do dostosowywania ustawień okna dialogowego w połączeniu z operatorem or bitowym. Wartość domyślna to FR_DOWN, która określa, że wyszukiwanie ma przebiegać w kierunku w dół. Zobacz [findreplace](/windows/win32/api/commdlg/ns-commdlg-findreplacew) struktury w windows SDK, aby uzyskać więcej informacji na temat tych flag.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego lub okna właściciela okna okna dialogowego. Jest to okno, które otrzyma specjalny komunikat wskazujący, że wymagane jest działanie znajdź/zamień. Jeśli null, używane jest główne okno aplikacji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt okna dialogowego został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby okno nadrzędne było powiadamiane o żądaniach znajdowania/zamieniania, należy użyć funkcji [Windows RegisterWindowMessage,](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) której wartość zwracana jest numerem wiadomości unikatowym dla wystąpienia aplikacji. Okno ramki powinien mieć wpis mapy wiadomości, który `OnFindReplace` deklaruje funkcję wywołania zwrotnego (w poniższym przykładzie), który obsługuje tę zarejestrowaną wiadomość. Poniższy fragment kodu jest przykładem tego, jak to `CMyRichEditView`zrobić dla klasy okna ramki o nazwie:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

W `OnFindReplace` ramach funkcji można interpretować intencje użytkownika przy użyciu [CFindReplaceDialog::FindNext](#findnext) i [CFindReplaceDialog::IsTerminating](#isterminating) metody i utworzyć kod dla operacji find/replace.

### <a name="example"></a>Przykład

  Zobacz przykład [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFindReplaceDialog::FindNext

Wywołanie tej funkcji z funkcji wywołania zwrotnego, aby ustalić, czy użytkownik chce znaleźć następne wystąpienie ciągu wyszukiwania.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik chce znaleźć następne wystąpienie ciągu wyszukiwania; w przeciwnym razie 0.

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFindReplaceDialog::GetFindString

Wywołanie tej funkcji z funkcji wywołania zwrotnego, aby pobrać ciąg domyślny, aby znaleźć.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślny ciąg do znalezienia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFindReplaceDialog::GetNotifier

Wywołanie tej funkcji powoduje pobranie wskaźnika do bieżącego okna dialogowego Znajdź zamień.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Lparam*<br/>
Wartość *lparam* przekazywane do funkcji `OnFindReplace` elementu członkowskiego okna ramki.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego okna dialogowego.

### <a name="remarks"></a>Uwagi

Powinien być używany w ramach funkcji wywołania zwrotnego, aby uzyskać dostęp `m_fr` do bieżącego okna dialogowego, wywołać jego funkcje członkowskie i uzyskać dostęp do struktury.

### <a name="example"></a>Przykład

Zobacz [CFindReplaceDialog::Create](#create) na przykład jak zarejestrować onfindReplace obsługi do odbierania powiadomień z okna dialogowego Znajdź zamień.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString

Wywołanie tej funkcji, aby pobrać bieżący ciąg wymiany.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślny ciąg, za pomocą którego można zastąpić znalezione ciągi.

### <a name="example"></a>Przykład

  Zobacz przykład [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFindReplaceDialog::IsTerminating

Wywołanie tej funkcji w ramach funkcji wywołania zwrotnego, aby ustalić, czy użytkownik podjął decyzję o zakończeniu okna dialogowego.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik zdecydował się zakończyć okno dialogowe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli ta funkcja zwraca wartość niezerową, należy wywołać funkcję `DestroyWindow` elementu członkowskiego bieżącego okna dialogowego i ustawić dowolną zmienną wskaźnika okna dialogowego na NULL. Opcjonalnie można również zapisać ostatnio wprowadzony tekst znajdowania/zamieniania i używać go do zainicjowania następnego okna dialogowego znajdowanie/zamienianie.

### <a name="example"></a>Przykład

  Zobacz przykład [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFindReplaceDialog::m_fr

Służy do dostosowywania `CFindReplaceDialog` obiektu.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Uwagi

`m_fr`jest strukturą typu [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Jego członkowie przechowują właściwości obiektu okna dialogowego. Po skonstruowaniu `CFindReplaceDialog` obiektu można `m_fr` użyć do zmodyfikowania różnych wartości w oknie dialogowym.

Aby uzyskać więcej informacji na `FINDREPLACE` temat tej struktury, zobacz strukturę w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFindReplaceDialog::MatchCase

Wywołanie tej funkcji, aby ustalić, czy użytkownik chce dokładnie dopasować przypadek find string.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik chce znaleźć wystąpienia ciągu wyszukiwania, które dokładnie pasują do przypadku ciągu wyszukiwania; w przeciwnym razie 0.

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord

Wywołanie tej funkcji, aby ustalić, czy użytkownik chce dopasować tylko całe słowa.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik chce dopasować tylko całe słowa ciągu wyszukiwania; w przeciwnym razie 0.

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFindReplaceDialog::ReplaceAll

Wywołanie tej funkcji, aby ustalić, czy użytkownik chce wszystkie wystąpienia ciągu do zastąpienia.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik zażądał, aby wszystkie ciągi pasujące do ciągu wymiany zostać zastąpione; w przeciwnym razie 0.

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent

Wywołanie tej funkcji, aby ustalić, czy użytkownik chce bieżącego wyrazu do zastąpienia.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik zażądał, aby aktualnie wybrany ciąg został zastąpiony ciągiem wymiany; w przeciwnym razie 0.

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFindReplaceDialog::SearchDown

Wywołanie tej funkcji, aby ustalić, czy użytkownik chce, aby wyszukiwanie kontynuować w kierunku w dół.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik chce, aby wyszukiwanie przebiegać w kierunku w dół; 0, jeśli użytkownik chce, aby wyszukiwanie przebiegać w górę.

## <a name="see-also"></a>Zobacz też

[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
