---
title: Klasa CFindReplaceDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 153653244534a1783b2b675f91216a8af3738e80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cfindreplacedialog-class"></a>Klasa CFindReplaceDialog
Umożliwia wdrożenie standardowego ciągu Znajdź/Zamień okien dialogowych w aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Wywołanie tej funkcji w celu utworzenia `CFindReplaceDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|Tworzy i wyświetla `CFindReplaceDialog` okno dialogowe.|  
|[CFindReplaceDialog::FindNext](#findnext)|Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce Znajdź następne wystąpienie ciągu wyszukiwania.|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|Wywołanie tej funkcji można pobrać bieżących parametrów wyszukiwania.|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Wywołanie tej funkcji można pobrać **FINDREPLACE** struktury programu obsługi wiadomości w zarejestrowany.|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Wywołanie tej funkcji można pobrać bieżącego Zastąp ciąg.|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|Wywołanie tej funkcji, aby określić, czy jest przerywany, okno dialogowe.|  
|[CFindReplaceDialog::MatchCase](#matchcase)|Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce wielkość liter w ciągu wyszukiwania są takie same.|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce dopasować tylko całe wyrazy.|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Wywołanie tej funkcji, aby ustalić, czy wszystkie wystąpienia ciągu mają zostać zastąpione przez użytkownika.|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce bieżącego słowa, które mają zostać zastąpione.|  
|[CFindReplaceDialog::SearchDown](#searchdown)|Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce wyszukiwania, aby kontynuować w dół kierunku.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|Struktury używane w celu dostosowania `CFindReplaceDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 W przeciwieństwie do innych Windows wspólne okna dialogowe `CFindReplaceDialog` obiekty są niemodalne, co pozwala użytkownikom na interakcję z innymi oknami, gdy są one na ekranie. Istnieją dwa rodzaje z `CFindReplaceDialog` obiektów: znajdowanie okien dialogowych i Znajdź i Zamień, okna dialogowe. Mimo że okien dialogowych Zezwalaj użytkownikowi na wejściowe wyszukiwania i wyszukiwania/zastępowania ciągów, nie wykonują wyszukiwania lub zastępowanie funkcji. Należy dodać je do aplikacji.  
  
 Aby utworzyć `CFindReplaceDialog` obiektów, użyj Konstruktora podana (który nie ma argumentów). Ponieważ jest niemodalne okno dialogowe, należy przydzielić obiektu przy użyciu sterty **nowe** operatora, a nie na stosie.  
  
 Raz `CFindReplaceDialog` obiekt został skonstruowany, należy wywołać [Utwórz](#create) funkcji członkowskiej, aby utworzyć i wyświetlić okno dialogowe.  
  
 Użyj [m_fr](#m_fr) struktury zainicjować okno dialogowe przed wywołaniem **Utwórz**. `m_fr` Struktura jest typu [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Aby uzyskać więcej informacji na tej struktury zobacz zestaw Windows SDK.  
  
 Aby okna nadrzędnego, który ma być powiadamiany o żądań Znajdź i Zamień, należy użyć systemu Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) funkcji i użyj [on_registered_message —](message-map-macros-mfc.md#on_registered_message) makra mapy wiadomości w sieci ramki okno obsługi tego komunikatu w zarejestrowany.  
  
 Można określić, czy użytkownik zdecydował się zakończyć okna dialogowego z `IsTerminating` funkcję elementu członkowskiego.  
  
 `CFindReplaceDialog`zależy od pliku COMMDLG. Plik DLL, która jest dostarczana z systemem Windows w wersji 3.1 lub nowszej.  
  
 Aby dostosować okno dialogowe, pochodzi z klasy `CFindReplaceDialog`, podaj szablon niestandardowe okno dialogowe i dodać mapy komunikatów do przetwarzania komunikatów powiadomień od formantów rozszerzonego. Komunikaty nieprzetworzone powinny zostać przekazane do klasy podstawowej.  
  
 Dostosowywanie funkcji punktów zaczepienia nie jest wymagane.  
  
 Aby uzyskać więcej informacji na temat używania `CFindReplaceDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog  
 Konstruuje `CFindReplaceDialog` obiektu.  
  
```  
CFindReplaceDialog();
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CFindReplaceDialog` obiekt jest niemodalne okno dialogowe, należy tworzyć na stercie przy użyciu `new` operatora.  
  
 Podczas niszczenia, próbuje wykonać platformę `delete this` na wskaźnik do okna dialogowego. Jeśli utworzono na stosie, okno dialogowe `this` wskaźnik nie istnieje i może spowodować niezdefiniowane zachowanie.  
  
 Aby uzyskać więcej informacji na temat konstrukcji `CFindReplaceDialog` obiekty, zobacz [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) omówienie. Użyj [CFindReplaceDialog::Create](#create) funkcji członkowskiej, aby wyświetlić okno dialogowe.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
##  <a name="create"></a>CFindReplaceDialog::Create  
 Tworzy i wyświetla Znajdź albo Znajdź/Zamień okna dialogowego pole obiektu, w zależności od wartości `bFindDialogOnly`.  
  
```  
virtual BOOL Create(
    BOOL bFindDialogOnly,  
    LPCTSTR lpszFindWhat,  
    LPCTSTR lpszReplaceWith = NULL,  
    DWORD dwFlags = FR_DOWN,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bFindDialogOnly`  
 Ustaw ten parametr, `TRUE` do wyświetlenia **znaleźć** okno dialogowe. Ustaw ją na `FALSE` do wyświetlenia **Znajdź/Zamień** okno dialogowe.  
  
 `lpszFindWhat`  
 Wskaźnik do domyślnego ciągu wyszukiwania, gdy zostanie wyświetlone okno dialogowe. Jeśli `NULL`, okno dialogowe nie zawiera domyślnego ciągu wyszukiwania.  
  
 `lpszReplaceWith`  
 Wskaźnik do domyślny ciąg zastępczy, gdy zostanie wyświetlone okno dialogowe. Jeśli `NULL`, okno dialogowe nie zawiera domyślny ciąg zastępczy.  
  
 `dwFlags`  
 Jedną lub więcej flag, które można dostosować ustawienia okna dialogowego łączyć przy użyciu bitowego operatora OR. Wartość domyślna to `FR_DOWN`, który określa, czy wyszukiwanie ma odbywać się w dół kierunku. Zobacz [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835) struktury w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat tych flag.  
  
 `pParentWnd`  
 Wskaźnik do okna nadrzędnego lub właściciela okna dialogowego. To okno zostanie wyświetlony komunikat specjalne wskazujący zażądano akcji Znajdź i Zamień. Jeśli `NULL`, jest używany w głównym oknie aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt — okno dialogowe został pomyślnie utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby okna nadrzędnego, który ma być powiadamiany o żądań Znajdź i Zamień, należy użyć systemu Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) funkcji, których wartość zwracana jest liczba wiadomości, unikatowe do wystąpienia aplikacji. Okna ramowe powinny mieć wpisu mapy komunikatów, który deklaruje funkcję wywołania zwrotnego ( `OnFindReplace` w następującym przykładzie) obsługująca tego komunikatu w zarejestrowany. Poniższy fragment kodu jest przykład tego, jak to zrobić w klasie okien ramowych, o nazwie `CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 W ramach Twojej `OnFindReplace` funkcji, interpretacji zamiarach użytkownika za pomocą [CFindReplaceDialog::FindNext](#findnext) i [CFindReplaceDialog::IsTerminating](#isterminating) metod i tworzy kod Znajdowanie i zamienianie operacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="findnext"></a>CFindReplaceDialog::FindNext  
 Wywołanie tej funkcji z funkcji wywołania zwrotnego do określenia, czy użytkownik chce Znajdź następne wystąpienie ciągu wyszukiwania.  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik chce Znajdź następne wystąpienie ciągu wyszukiwania; w przeciwnym razie 0.  
  
##  <a name="getfindstring"></a>CFindReplaceDialog::GetFindString  
 Wywołanie tej funkcji z funkcji wywołania zwrotnego można pobrać domyślny ciąg można znaleźć.  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślny ciąg, który można znaleźć.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getnotifier"></a>CFindReplaceDialog::GetNotifier  
 Wywołanie tej funkcji można pobrać wskaźnik do bieżące okno dialogowe Znajdź Zastąp.  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `lParam`  
 **Lparam** wartość przekazywana do okno ramowe **OnFindReplace** funkcję elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Tej opcji należy używać w ramach funkcji wywołania zwrotnego dostęp do bieżącej okno dialogowe, wywołaj jego elementów członkowskich, funkcje i dostępu `m_fr` struktury.  
  
### <a name="example"></a>Przykład  
 Zobacz [CFindReplaceDialog::Create](#create) na przykład można zarejestrować obsługi OnFindReplace, aby otrzymywać powiadomienia w oknie dialogowym Znajdowanie zastąpić.  
  
 [!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString  
 Wywołanie tej funkcji można pobrać bieżącego Zastąp ciąg.  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślny ciąg z którego ma zostać zamieniony znaleziony ciągów.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="isterminating"></a>CFindReplaceDialog::IsTerminating  
 Wywołanie tej funkcji w funkcji wywołania zwrotnego, aby określić, czy użytkownik zdecydował się zakończyć okna dialogowego.  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik zdecydował się zakończyć okno dialogowe; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta funkcja zwraca wartość niezerową, należy wywołać `DestroyWindow` funkcji członkowskiej klasy bieżące okno dialogowe i wszelkie dialogowym zmiennej wskaźnikowej do zestawu **NULL**. Opcjonalnie również przechowywanie tekstu Znajdź/Zamień ostatnio wprowadzonego i umożliwia inicjowanie następnym oknie dialogowym Znajdowanie i zamienianie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::GetFindString](#getfindstring).  
  
##  <a name="m_fr"></a>CFindReplaceDialog::m_fr  
 Używane w celu dostosowania `CFindReplaceDialog` obiektu.  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_fr`jest to struktura typu [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835). Jej elementów członkowskich magazynu właściwości obiektu okno dialogowe. Po konstruowania `CFindReplaceDialog` obiektu, można użyć `m_fr` do modyfikowania różnych wartości w oknie dialogowym.  
  
 Aby uzyskać więcej informacji na tej struktury, zobacz **FINDREPLACE** struktury w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).  
  
##  <a name="matchcase"></a>CFindReplaceDialog::MatchCase  
 Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce wielkość liter w ciągu wyszukiwania są takie same.  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik chce, aby wyszukać wystąpienia ciąg wyszukiwania, które dokładnie odpowiadać wielkość liter w ciągu wyszukiwania; w przeciwnym razie 0.  
  
##  <a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord  
 Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce dopasować tylko całe wyrazy.  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik chce dopasować tylko całe wyrazy wyszukiwanego ciągu; w przeciwnym razie 0.  
  
##  <a name="replaceall"></a>CFindReplaceDialog::ReplaceAll  
 Wywołanie tej funkcji, aby ustalić, czy wszystkie wystąpienia ciągu mają zostać zastąpione przez użytkownika.  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik zażąda, czy należy zastąpić wszystkie ciągi dopasowywania ciągu Zamień; w przeciwnym razie 0.  
  
##  <a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent  
 Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce bieżącego słowa, które mają zostać zastąpione.  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik zażądał, że aktualnie zaznaczony ciąg zamieniony ciąg Zamień; w przeciwnym razie 0.  
  
##  <a name="searchdown"></a>CFindReplaceDialog::SearchDown  
 Wywołanie tej funkcji w celu ustalenia, czy użytkownik chce wyszukiwania, aby kontynuować w dół kierunku.  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik chce wyszukiwania, aby kontynuować w dół kierunku; 0, jeśli użytkownik chce wyszukiwania, aby przejść w górę kierunku.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)  
