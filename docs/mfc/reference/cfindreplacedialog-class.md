---
title: Klasa okno CFindReplaceDialog
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
ms.openlocfilehash: 92429bc17301d6615c87de958f38a717528e9544
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212439"
---
# <a name="cfindreplacedialog-class"></a>Klasa okno CFindReplaceDialog

Pozwala zaimplementować standardowe okna dialogowe szukania/zamieniania ciągów w aplikacji.

## <a name="syntax"></a>Składnia

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Okno CFindReplaceDialog:: okno CFindReplaceDialog](#cfindreplacedialog)|Wywołaj tę funkcję, aby skonstruować `CFindReplaceDialog` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Okno CFindReplaceDialog:: Create](#create)|Tworzy i wyświetla okno `CFindReplaceDialog` dialogowe.|
|[Okno CFindReplaceDialog:: ZnajdźNastępny](#findnext)|Wywołaj tę funkcję, aby określić, czy użytkownik chce znaleźć następne wystąpienie ciągu wyszukiwania.|
|[Okno CFindReplaceDialog:: getfindstr](#getfindstring)|Wywołaj tę funkcję, aby pobrać bieżący ciąg wyszukiwania.|
|[Okno CFindReplaceDialog:: getpowiadamianie](#getnotifier)|Wywołaj tę funkcję, aby pobrać `FINDREPLACE` strukturę z zarejestrowanego programu obsługi komunikatów.|
|[Okno CFindReplaceDialog:: GetReplaceString](#getreplacestring)|Wywołaj tę funkcję, aby pobrać bieżący ciąg zamiany.|
|[Okno CFindReplaceDialog:: iskończona](#isterminating)|Wywołaj tę funkcję, aby określić, czy okno dialogowe zostało zakończone.|
|[Okno CFindReplaceDialog:: MatchCase](#matchcase)|Wywołaj tę funkcję, aby określić, czy użytkownik chce dokładnie dopasować do wielkości liter w wyszukiwanym ciągu.|
|[Okno CFindReplaceDialog:: MatchWholeWord](#matchwholeword)|Wywołaj tę funkcję, aby określić, czy użytkownik chce dopasować tylko całe wyrazy.|
|[Okno CFindReplaceDialog:: Zamień wszystkie](#replaceall)|Wywołaj tę funkcję, aby określić, czy użytkownik chce, aby wszystkie wystąpienia ciągu zostały zastąpione.|
|[Okno CFindReplaceDialog:: ReplaceCurrent](#replacecurrent)|Wywołaj tę funkcję, aby określić, czy użytkownik chce zastąpić bieżące słowo.|
|[Okno CFindReplaceDialog:: SearchDown](#searchdown)|Wywołaj tę funkcję, aby określić, czy użytkownik chce, aby wyszukiwanie kontynuowało pracę w kierunku do dołu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Okno CFindReplaceDialog:: m_fr](#m_fr)|Struktura używana do dostosowywania `CFindReplaceDialog` obiektu.|

## <a name="remarks"></a>Uwagi

W przeciwieństwie do innych okien dialogowych wspólnych okien `CFindReplaceDialog` obiekty są niemodalne, dzięki czemu użytkownicy mogą korzystać z innych okien, gdy znajdują się na ekranie. Istnieją dwa rodzaje `CFindReplaceDialog` obiektów: okna dialogowe Znajdowanie i znajdowanie/zamienianie okien dialogowych. Mimo że okna dialogowe umożliwiają użytkownikowi wprowadzanie danych wyszukiwania i wyszukiwanie/zamienianie ciągów, nie wykonują żadnych funkcji wyszukiwania ani zamiany. Należy dodać je do aplikacji.

Aby skonstruować `CFindReplaceDialog` obiekt, użyj dostarczonego konstruktora (który nie ma argumentów). Ponieważ jest to niemodalne okno dialogowe, Przydziel obiekt na stercie przy użyciu **`new`** operatora, a nie na stosie.

Gdy `CFindReplaceDialog` obiekt został skonstruowany, należy wywołać funkcję [tworzenia](#create) elementu członkowskiego, aby utworzyć i wyświetlić okno dialogowe.

Użyj struktury [m_fr](#m_fr) , aby zainicjować okno dialogowe przed wywołaniem `Create` . `m_fr`Struktura jest typu [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Aby uzyskać więcej informacji na temat tej struktury, zobacz Windows SDK.

Aby okno nadrzędne było powiadamiane o żądaniach wyszukiwania/zamieniania, należy użyć funkcji [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) systemu Windows i użyć makra [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) -map komunikatu w oknie ramki, które obsługuje ten zarejestrowany komunikat.

Można określić, czy użytkownik zdecydował się zakończyć okno dialogowe z `IsTerminating` funkcją składową.

`CFindReplaceDialog`opiera się na pliku COMMDLG.DLL, który jest dostarczany z systemem Windows w wersji 3,1 lub nowszej.

Aby dostosować okno dialogowe, wyprowadzić klasę z `CFindReplaceDialog` , udostępnić niestandardowy szablon okna dialogowego i dodać mapę komunikatów do przetwarzania komunikatów powiadomień z formantów rozszerzonych. Wszystkie nieprzetworzone komunikaty powinny być przesyłane do klasy bazowej.

Dostosowywanie funkcji Hook nie jest wymagane.

Aby uzyskać więcej informacji na temat korzystania z programu `CFindReplaceDialog` , zobacz [wspólne klasy okien dialogowych](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs. h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>Okno CFindReplaceDialog:: okno CFindReplaceDialog

Konstruuje `CFindReplaceDialog` obiekt.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Uwagi

Ponieważ `CFindReplaceDialog` obiekt jest niemodalnym oknem dialogowym, należy skonstruować go na stercie przy użyciu **`new`** operatora.

Podczas niszczenia, struktura próbuje wykonać operację **usuwania** na wskaźniku do okna dialogowego. Jeśli utworzono okno dialogowe na stosie, **`this`** wskaźnik nie istnieje i może to spowodować niezdefiniowane zachowanie.

Aby uzyskać więcej informacji na temat konstruowania `CFindReplaceDialog` obiektów, zobacz Omówienie [okno CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) . Użyj funkcji [okno CFindReplaceDialog:: Create](#create) member, aby wyświetlić okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>Okno CFindReplaceDialog:: Create

Tworzy i wyświetla obiekt okna dialogowego Znajdź lub Znajdź/Zamień, w zależności od wartości `bFindDialogOnly` .

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bFindDialogOnly*<br/>
Ustaw ten parametr na wartość TRUE, aby wyświetlić okno dialogowe **Znajdowanie** . Ustaw na wartość FALSE, aby wyświetlić okno dialogowe **Znajdowanie/zamienianie** .

*lpszFindWhat*<br/>
Wskaźnik na domyślny ciąg wyszukiwania, gdy zostanie wyświetlone okno dialogowe. Jeśli wartość jest równa NULL, okno dialogowe nie zawiera domyślnego ciągu wyszukiwania.

*lpszReplaceWith*<br/>
Wskaźnik na domyślny ciąg zastępczy po wyświetleniu okna dialogowego. Jeśli wartość jest równa NULL, okno dialogowe nie zawiera domyślnego ciągu zastępczego.

*flagiDW*<br/>
Jedna lub więcej flag, których można użyć, aby dostosować ustawienia okna dialogowego połączone przy użyciu operatora bitowego or. Wartość domyślna to FR_DOWN, co oznacza, że wyszukiwanie ma przechodzić w kierunku do dołu. Zapoznaj się ze strukturą [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) w Windows SDK, aby uzyskać więcej informacji na temat tych flag.

*pParentWnd*<br/>
Wskaźnik do okna dialogowego nadrzędnego lub właściciela. Jest to okno, w którym zostanie wyświetlony specjalny komunikat informujący o tym, że zażądano akcji Znajdź/Zamień. Jeśli wartość jest równa NULL, używane jest główne okno aplikacji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt okna dialogowego został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby okno nadrzędne było powiadamiane o żądaniach wyszukiwania/zamieniania, należy użyć funkcji [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) systemu Windows, której wartość zwracana jest numerem wiadomości unikatowym dla wystąpienia aplikacji. Okno ramki powinno mieć wpis mapy komunikatów, który deklaruje funkcję wywołania zwrotnego ( `OnFindReplace` w poniższym przykładzie), która obsługuje ten zarejestrowany komunikat. Poniższy fragment kodu jest przykładem, jak to zrobić dla klasy okien ramowych o nazwie `CMyRichEditView` :

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

W ramach `OnFindReplace` funkcji interpretuje intencje użytkownika przy użyciu metod [okno CFindReplaceDialog:: ZnajdźNastępny](#findnext) i [okno CFindReplaceDialog::](#isterminating) isabort i tworzysz kod dla operacji znajdowania/zamieniania.

### <a name="example"></a>Przykład

  Zobacz przykład dla [okno CFindReplaceDialog:: okno CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>Okno CFindReplaceDialog:: ZnajdźNastępny

Wywołaj tę funkcję z funkcji wywołania zwrotnego, aby określić, czy użytkownik chce znaleźć następne wystąpienie ciągu wyszukiwania.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik chce znaleźć następne wystąpienie ciągu wyszukiwania; w przeciwnym razie 0.

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>Okno CFindReplaceDialog:: getfindstr

Wywołaj tę funkcję z funkcji wywołania zwrotnego, aby pobrać domyślny ciąg do znalezienia.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślny ciąg do znalezienia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>Okno CFindReplaceDialog:: getpowiadamianie

Wywołaj tę funkcję, aby pobrać wskaźnik do bieżącego okna dialogowego Znajdź Zastąp.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*lParam*<br/>
Wartość *lParam* przeniesiona do `OnFindReplace` funkcji składowej okna ramki.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego okna dialogowego.

### <a name="remarks"></a>Uwagi

Powinien być używany w funkcji wywołania zwrotnego, aby uzyskać dostęp do bieżącego okna dialogowego, wywołać jego funkcje członkowskie i uzyskać dostęp do `m_fr` struktury.

### <a name="example"></a>Przykład

Zobacz [okno CFindReplaceDialog:: Create](#create) , aby zapoznać się z przykładem sposobu rejestrowania procedury obsługi OnFindReplace w celu otrzymywania powiadomień z okna dialogowego Znajdowanie zastąpień.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>Okno CFindReplaceDialog:: GetReplaceString

Wywołaj tę funkcję, aby pobrać bieżący ciąg zamiany.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślny ciąg, za pomocą którego ma zostać zamieniony znaleziony ciąg.

### <a name="example"></a>Przykład

  Zobacz przykład dla [okno CFindReplaceDialog:: Getfindstrs](#getfindstring).

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>Okno CFindReplaceDialog:: iskończona

Wywołaj tę funkcję w funkcji wywołania zwrotnego, aby określić, czy użytkownik zdecydował się zakończyć okno dialogowe.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik zdecydował się zakończyć okno dialogowe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli ta funkcja zwróci wartość różną od zera, należy wywołać `DestroyWindow` funkcję członkowską bieżącego okna dialogowego i ustawić zmienną wskaźnika okna dialogowego na null. Opcjonalnie możesz również przechowywać ostatnio wprowadzony tekst Znajdź/Zamień i użyć go do zainicjowania następnego okna dialogowego Znajdowanie/zamienianie.

### <a name="example"></a>Przykład

  Zobacz przykład dla [okno CFindReplaceDialog:: Getfindstrs](#getfindstring).

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>Okno CFindReplaceDialog:: m_fr

Służy do dostosowywania `CFindReplaceDialog` obiektu.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Uwagi

`m_fr`jest strukturą typu [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Jego członkowie przechowują charakterystykę obiektu okna dialogowego. Po skonstruowaniu `CFindReplaceDialog` obiektu można użyć `m_fr` programu, aby zmodyfikować różne wartości w oknie dialogowym.

Aby uzyskać więcej informacji na temat tej struktury, zobacz `FINDREPLACE` strukturę w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [okno CFindReplaceDialog:: okno CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>Okno CFindReplaceDialog:: MatchCase

Wywołaj tę funkcję, aby określić, czy użytkownik chce dokładnie dopasować do wielkości liter w wyszukiwanym ciągu.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik chce znaleźć wystąpienia ciągu wyszukiwania, który dokładnie pasuje do wielkości liter ciągu wyszukiwania; w przeciwnym razie 0.

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>Okno CFindReplaceDialog:: MatchWholeWord

Wywołaj tę funkcję, aby określić, czy użytkownik chce dopasować tylko całe wyrazy.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik chce dopasować tylko całe wyrazy ciągu wyszukiwania; w przeciwnym razie 0.

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>Okno CFindReplaceDialog:: Zamień wszystkie

Wywołaj tę funkcję, aby określić, czy użytkownik chce, aby wszystkie wystąpienia ciągu zostały zastąpione.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik zażądał zastąpienia wszystkich ciągów, które pasują do ciągu zamiany; w przeciwnym razie 0.

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>Okno CFindReplaceDialog:: ReplaceCurrent

Wywołaj tę funkcję, aby określić, czy użytkownik chce zastąpić bieżące słowo.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli użytkownik zażądał zastąpienia aktualnie wybranego ciągu ciągiem zastępującym; w przeciwnym razie 0.

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>Okno CFindReplaceDialog:: SearchDown

Wywołaj tę funkcję, aby określić, czy użytkownik chce, aby wyszukiwanie kontynuowało pracę w kierunku do dołu.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik chce, aby wyszukiwanie przejdzie w kierunku ku dolnym; 0, jeśli użytkownik chce, aby wyszukiwanie kontynuowało pracę w kierunku do góry.

## <a name="see-also"></a>Zobacz także

[Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
