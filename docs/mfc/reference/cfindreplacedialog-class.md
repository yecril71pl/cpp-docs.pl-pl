---
title: Klasa CFindReplaceDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c88a517d600536d4f89b1621e225ad80666885a
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338652"
---
# <a name="cfindreplacedialog-class"></a>Klasa CFindReplaceDialog
Umożliwia wdrożenie okien dialogowych standardowego ciągu Znajdź/Zamień w aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Wywołaj tę funkcję, aby skonstruować `CFindReplaceDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|Tworzy i wyświetla `CFindReplaceDialog` okno dialogowe.|  
|[CFindReplaceDialog::FindNext](#findnext)|Wywołaj tę funkcję, aby ustalić, czy użytkownik chce, aby znaleźć następne wystąpienie ciągu wyszukiwania.|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|Wywołaj tę funkcję można pobrać bieżącego ciągu wyszukiwania.|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Wywołaj tę funkcję, aby pobrać `FINDREPLACE` strukturze usługi program obsługi zarejestrowanych komunikatów.|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Wywołaj tę funkcję można pobrać bieżącego ciągu zastępowania.|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|Wywołaj tę funkcję, aby ustalić, czy jest przerywany, okno dialogowe.|  
|[CFindReplaceDialog::MatchCase](#matchcase)|Wywołaj tę funkcję, aby ustalić, czy użytkownik chce, aby dokładnie odpowiadać wielkości liter w ciągu wyszukiwania.|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Wywołaj tę funkcję, aby ustalić, czy użytkownik chce, aby dopasować tylko całe wyrazy.|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Wywołaj tę funkcję, aby ustalić, czy użytkownik chce, aby wszystkie wystąpienia ciągu, który ma zostać zastąpione.|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Wywołaj tę funkcję, aby ustalić, czy użytkownik chce bieżącego słowa, które ma zostać zastąpione.|  
|[CFindReplaceDialog::SearchDown](#searchdown)|Wywołaj tę funkcję, aby ustalić, czy użytkownik chce wyszukiwania, aby przejść w kierunku w dół.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|Struktury używane w celu dostosowania `CFindReplaceDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 W przeciwieństwie do innych Windows typowych okien dialogowych `CFindReplaceDialog` obiekty są niemodalne, pozwalając użytkownikom na interakcję z innymi oknami, gdy są one na ekranie. Istnieją dwa rodzaje z `CFindReplaceDialog` obiektów: znajdowanie okien dialogowych i okna dialogowe Znajdź i Zamień. Mimo że okna dialogowe zezwala użytkownikowi na wyszukiwanie danych wejściowych i ciągi wyszukiwania/zastępowania, nie wykonują wyszukiwanie lub zastępując funkcji. Należy dodać je do aplikacji.  
  
 Do konstruowania `CFindReplaceDialog` obiektu, należy użyć konstruktora podana, (która nie ma argumentów). Ponieważ jest niemodalne okno dialogowe, należy przydzielić obiektu przy użyciu sterty **nowe** operatora, a nie na stosie.  
  
 Raz `CFindReplaceDialog` obiekt został skonstruowany, musisz użyć wywołania [Utwórz](#create) funkcja elementu członkowskiego, aby utworzyć i wyświetlić okno dialogowe.  
  
 Użyj [m_fr](#m_fr) strukturę, aby zainicjować okno dialogowe przed wywołaniem `Create`. `m_fr` Struktury jest typu [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Aby uzyskać więcej informacji na temat tej struktury zobacz zestaw Windows SDK.  
  
 Aby okno nadrzędne otrzymywać powiadomienia, Znajdź/Zamień żądań, należy użyć Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) działać, a następnie użyć [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) makra mapy komunikatów w swojej ramki okno, który obsługuje ten zarejestrowany komunikat.  
  
 Można określić, czy użytkownik zdecydował się zakończyć okno dialogowe z `IsTerminating` funkcja elementu członkowskiego.  
  
 `CFindReplaceDialog` opiera się na pliku COMMDLG. Plik DLL, który jest dostarczany z programem Windows w wersji 3.1 lub nowszej.  
  
 Aby dostosować okno dialogowe, należy wyprowadzić klasę z `CFindReplaceDialog`, udostępniają szablon niestandardowy dialog i dodać mapy wiadomości, przetwarzanie komunikatów powiadomień od formantów rozszerzonego. Wszystkie nieprzetworzone komunikaty powinien zostać przekazany do klasy bazowej.  
  
 Dostosowywanie funkcji punktów zaczepienia nie jest wymagana.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CFindReplaceDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog  
 Konstruuje `CFindReplaceDialog` obiektu.  
  
```  
CFindReplaceDialog();
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CFindReplaceDialog` obiektu jest niemodalne okno dialogowe, należy tworzyć na stosie przy użyciu **nowe** operatora.  
  
 Podczas niszczenia, próbuje wykonać ramach **usunąć ten** wskaźnika do okna dialogowego. Jeśli okno dialogowe są tworzone na stosie, **to** wskaźnik nie istnieje i może spowodować niezdefiniowane zachowanie.  
  
 Aby uzyskać więcej informacji na temat konstrukcji `CFindReplaceDialog` obiekty, zobacz [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) Przegląd. Użyj [CFindReplaceDialog::Create](#create) funkcja elementu członkowskiego, aby wyświetlić okno dialogowe.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
##  <a name="create"></a>  CFindReplaceDialog::Create  
 Tworzy i wyświetla Znajdź lub Znajdź/Zamień okna dialogowego pole obiektu, w zależności od wartości `bFindDialogOnly`.  
  
```  
virtual BOOL Create(
    BOOL bFindDialogOnly,  
    LPCTSTR lpszFindWhat,  
    LPCTSTR lpszReplaceWith = NULL,  
    DWORD dwFlags = FR_DOWN,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *bFindDialogOnly*  
 Ustaw ten parametr na wartość TRUE, aby wyświetlić **znaleźć** okno dialogowe. Ustaw ją na wartość FALSE, aby wyświetlić **Znajdź/Zamień** okno dialogowe.  
  
 *lpszFindWhat*  
 Wskaźnik na domyślny ciąg wyszukiwania, gdy pojawi się okno dialogowe. Jeśli ma wartość NULL, okno dialogowe nie zawiera domyślny ciąg wyszukiwania.  
  
 *lpszReplaceWith*  
 Wskaźnik do ciągu zamiennym domyślną, gdy pojawi się okno dialogowe. Jeśli ma wartość NULL, okno dialogowe nie zawiera domyślny ciąg zastępczy.  
  
 *Flagidw*  
 Co najmniej jeden flagi, których można użyć, aby dostosować ustawienia okna dialogowego łączyć przy użyciu bitowego operatora OR. Wartość domyślna to FR_DOWN, która określa, że wyszukiwanie postępować w kierunku w dół. Zobacz [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835) struktury w zestawie Windows SDK, aby uzyskać więcej informacji na temat tych flag.  
  
 *pParentWnd*  
 Wskaźnik do okna nadrzędnego lub właściciela okno dialogowe. To okno, które otrzymają specjalne komunikat wskazujący, żądanie akcji Znajdź/Zamień. Jeśli ma wartość NULL, jest używany w głównym oknie aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli obiekt okno dialogowe został pomyślnie utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby okno nadrzędne otrzymywać powiadomienia, Znajdź/Zamień żądań, należy użyć Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) funkcji, których wartość zwracana jest liczba wiadomości, unikatowe dla wystąpienia aplikacji. Okno ramki powinny mieć wpisu mapy wiadomości, która deklaruje funkcję wywołania zwrotnego ( `OnFindReplace` w poniższym przykładzie) obsługującego ten zarejestrowany komunikat. Poniższy fragment kodu znajduje się przykład jak to zrobić w klasie okien ramowych, o nazwie `CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 W ramach Twojej `OnFindReplace` funkcji interpretacji zamiarach użytkownika przy użyciu [CFindReplaceDialog::FindNext](#findnext) i [CFindReplaceDialog::IsTerminating](#isterminating) metody i możesz utworzyć kod dla operacji Znajdź i Zamień.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="findnext"></a>  CFindReplaceDialog::FindNext  
 Wywołaj tę funkcję ze swojej funkcji wywołania zwrotnego, aby ustalić, czy użytkownik chce, aby znaleźć następne wystąpienie ciągu wyszukiwania.  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik chce, aby znaleźć następne wystąpienie ciągu wyszukiwania; w przeciwnym razie 0.  
  
##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString  
 Wywołaj tę funkcję można pobrać domyślny ciąg można znaleźć funkcji wywołania zwrotnego.  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślny ciąg, który można znaleźć.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier  
 Wywołaj tę funkcję, aby pobrać wskaźnika do bieżącego Znajdź Zastąp okna dialogowego.  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 *lParam*  
 *Lparam* wartość przekazywana do okno ramowe `OnFindReplace` funkcja elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Należy jej używać w ramach funkcji wywołania zwrotnego dostęp do bieżącego okna dialogowego, wywołaj członków, funkcje i dostęp `m_fr` struktury.  
  
### <a name="example"></a>Przykład  
 Zobacz [CFindReplaceDialog::Create](#create) przykładowy sposób rejestrowania procedury obsługi OnFindReplace może otrzymywać powiadomienia z okna dialogowego Znajdowanie Zastąp.  
  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString  
 Wywołaj tę funkcję można pobrać bieżącego ciągu zastępowania.  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślny ciąg za pomocą którego ma zostać znaleziona ciągów.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating  
 Wywołaj tę funkcję w ramach funkcji wywołania zwrotnego do określenia, czy użytkownik zdecydował się do zakończenia okna dialogowego.  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik zdecydował się zakończyć w oknie dialogowym. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta funkcja zwraca wartość różną od zera, należy wywołać `DestroyWindow` funkcji składowej typu bieżącego okna dialogowego pole, a następnie ustaw dowolnej zmiennej wskaźnika okno dialogowe na wartość NULL. Opcjonalnie możesz również przechowywanie tekstu Znajdź/Zamień ostatnio wprowadzonego i użyć go, aby zainicjować okno dialogowe Znajdź/Zamień następny.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr  
 Używany w celu dostosowania `CFindReplaceDialog` obiektu.  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_fr` jest to struktura typu [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Jego członkowie przechowywać właściwości obiektu, okno dialogowe. Po konstruowanie `CFindReplaceDialog` obiektu, możesz użyć `m_fr` do modyfikowania różnych wartości w oknie dialogowym.  
  
 Aby uzyskać więcej informacji na temat tej struktury, zobacz `FINDREPLACE` struktury w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase  
 Wywołaj tę funkcję, aby ustalić, czy użytkownik chce, aby dokładnie odpowiadać wielkości liter w ciągu wyszukiwania.  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik chce, aby wyszukać wystąpienia ciągu wyszukiwania, które dokładnie odpowiadać wielkości liter w ciągu wyszukiwania; w przeciwnym razie 0.  
  
##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord  
 Wywołaj tę funkcję, aby ustalić, czy użytkownik chce, aby dopasować tylko całe wyrazy.  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik chce dopasować tylko całe wyrazy ciąg wyszukiwania; w przeciwnym razie 0.  
  
##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll  
 Wywołaj tę funkcję, aby ustalić, czy użytkownik chce, aby wszystkie wystąpienia ciągu, który ma zostać zastąpione.  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik zażądał, czy należy zastąpić wszystkie ciągi dopasowania ciągu zastępowania; w przeciwnym razie 0.  
  
##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent  
 Wywołaj tę funkcję, aby ustalić, czy użytkownik chce bieżącego słowa, które ma zostać zastąpione.  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik zażądał, że zaznaczony ciąg zastąpione ciągu zastępowania; w przeciwnym razie 0.  
  
##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown  
 Wywołaj tę funkcję, aby ustalić, czy użytkownik chce wyszukiwania, aby przejść w kierunku w dół.  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik chce, wyszukiwanie, aby przejść w dół kierunku; 0, jeśli użytkownik chce wyszukiwania, aby przejść w górę kierunku.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)  
