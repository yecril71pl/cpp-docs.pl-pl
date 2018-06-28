---
title: Klasa CKeyboardManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
dev_langs:
- C++
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27ff8f622eb3af52ad23f8f4fc7a20ecb8be9b77
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041139"
---
# <a name="ckeyboardmanager-class"></a>Klasa CKeyboardManager
Zarządza skrótów tabel klucza głównego okna ramowego i podrzędnych okien ramowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CKeyboardManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Konstruuje `CKeyboardManager` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CKeyboardManager::CleanUp](#cleanup)|Czyści w tabelach klawiszy skrótów.|  
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Pobiera domyślny klawisz skrótu dla określonego polecenia i okna.|  
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Określa, czy klucz jest obsługiwany przez tabeli akceleratora.|  
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Wskazuje, czy znak jest do druku.|  
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Wskazuje, czy menu Pokaż klawisze skrótów dla polecenia lub klawisz skrótu domyślne.|  
|[CKeyboardManager::LoadState](#loadstate)|Ładuje w tabelach klawiszy skrótów z rejestru systemu Windows.|  
|[CKeyboardManager::ResetAll](#resetall)|Ponowne ładowanie tabel klucza skrótu z zasobów aplikacji.|  
|[CKeyboardManager::SaveState](#savestate)|Zapisuje skrót tabel klucza rejestru systemu Windows.|  
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Określa, czy platformę Wyświetla wszystkie klawisze skrótów dla wszystkich poleceń lub klawisza skrótu jednej dla każdego polecenia. Ta metoda nie ma wpływu na polecenia, które mają tylko jeden klawisz skrótu skojarzony.|  
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Konwertuje znak na jego górnej rejestru.|  
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizuje tabeli klawiszy skrótów nowej tabeli klawiszy skrótów.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej klasy pozwalają na zapisywanie i załadować tabel klawiszy skrótów do rejestru systemu Windows, użyj szablonu w celu aktualizacji w tabelach klawiszy skrótów i znaleźć domyślny klawisz skrótu polecenia w oknie ramowym. Ponadto `CKeyboardManager` obiektu pozwala kontrolować sposób wyświetlania klawiszy skrótów do użytkownika.  
  
 Nie należy tworzyć `CKeyboardManager` obiekt ręcznie. Go zostaną utworzone automatycznie w ramach aplikacji. Jednak należy wywołać [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) podczas procesu inicjowania aplikacji. Aby uzyskać wskaźnika menedżera klawiatury dla aplikacji, należy wywołać [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać wskaźnik do `CKeyboardManager` obiekt z `CWinAppEx` klasy i sposób wyświetlania klawiszy skrótów skojarzone z poleceń menu. Następujący fragment kodu jest częścią [próbki niestandardowych stron](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxkeyboardmanager.h  
  
##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager  
 Konstruuje `CKeyboardManager` obiektu.  
  
```  
CKeyboardManager();
```  
  
### <a name="remarks"></a>Uwagi  
 W większości przypadków, nie trzeba tworzyć `CKeyboardManager` bezpośrednio. Domyślnie platformę tworzy ją. Aby uzyskać wskaźnik do `CKeyboardManager`, wywołaj [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Jeśli można utworzyć ręcznie, należy go zainicjować z metodą [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).  
  
##  <a name="cleanup"></a>  CKeyboardManager::CleanUp  
 Zwalnia `CKeyboardManager` zasobów i usuwa wszystkie mapowania klawiszy skrótów.  
  
```  
static void CleanUp();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat klawiszy skrótów, zobacz [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md).  
  
 Nie masz wywołanie tej funkcji, gdy aplikacja kończy pracę, ponieważ struktura wywołuje ona automatycznie podczas zamknięcie aplikacji.  
  
##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator  
 Pobiera domyślny klawisz skrótu dla określonego polecenia i okna.  
  
```  
static BOOL FindDefaultAccelerator(
    UINT uiCmd,  
    CString& str,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiCmd*  
 Identyfikator polecenia.  
  
 [out] *str*  
 Odwołanie do `CString` obiektu.  
  
 [in] *pWndFrame*  
 Wskaźnik do ramki okna.  
  
 [in] *bIsDefaultFrame*  
 Określa, czy okno ramowe domyślnego ramki okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli skrót zostanie odnaleziony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wyszukuje określone przez polecenie *uiCmd* i pobiera domyślny klucz skrótów. Następnie metoda pobiera parametry skojarzone z tym klawisz skrótu i zapisuje wartość *str* parametru.  
  
##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled  
 Określa, czy określony klucz jest obsługiwany przez [CKeyboardManager klasy](../../mfc/reference/ckeyboardmanager-class.md).  
  
```  
static BOOL __stdcall IsKeyHandled(
    WORD nKey,  
    BYTE fVirt,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *nKey*|Klucz do sprawdzenia.|  
|[in] *fVirt*|Określa zachowanie klawisza skrótu. Aby uzyskać listę możliwych wartości, zobacz [struktury AKCELERACJA](http://msdn.microsoft.com/library/windows/desktop/ms646340).|  
|[in] *pWndFrame*|Okno ramowe. Ta metoda określa, czy klawisz skrótu jest obsługiwana w tej ramce.|  
|[in] *bIsDefaultFrame*|Parametrów typu Boolean, która wskazuje, czy *pWndFrame* jest domyślnego ramki okna.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli klawisz skrótu jest obsługiwane. `FALSE` Jeśli klucz nie jest obsługiwana lub *pWndFrame* jest `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Parametry wejściowe muszą być zgodne wpisu tabeli akceleratora zarówno dla *nKey* i *fVirt* ustalenie, czy klawisz skrótu jest obsługiwana w *pWndFrame*.  
  
##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable  
 Wskazuje, czy znak jest do druku.  
  
```  
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *nChar*|Ta metoda sprawdza znak.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znak jest drukowania, zero, jeśli nie jest.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli wywołanie [GetKeyboardState](http://msdn.microsoft.com/library/windows/desktop/ms646299) nie powiedzie się.  
  
##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators  
 Wskazuje, czy menu Pokaż klawisze skrótu skojarzony z poleceń menu lub klawiszy skrótów domyślne.  
  
```  
static BOOL IsShowAllAccelerators();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli aplikacja wyświetla listę wszystkich klawiszy skrótów do poleceń menu; 0, jeśli aplikacja wyświetla tylko domyślny klawiszy skrótów.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacja wyświetla listę klawiszy skrótów do poleceń menu na pasku menu. Użyj funkcji [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) do kontrolowania czy aplikacji zawiera listę wszystkich klawiszy skrótów lub po prostu domyślne klawiszy skrótu.  
  
##  <a name="loadstate"></a>  CKeyboardManager::LoadState  
 Ładuje w tabelach klawiszy skrótów z rejestru systemu Windows.  
  
```  
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszProfileName*  
 Ścieżka rejestru gdzie `CKeyboardManager` dane są zapisywane.  
  
 [in] *pDefaultFrame*  
 Wskaźnik do okno ramowe ma być używana jako domyślnego okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli stan został pomyślnie załadowany lub równa 0 w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *lpszProfileName* parametr jest `NULL`, ta metoda sprawdza domyślnej lokalizacji rejestru `CKeyboardManager` danych. Domyślna lokalizacja rejestru jest określona przez [CWinAppEx klasy](../../mfc/reference/cwinappex-class.md). Dane muszą być wcześniej zapisane przy użyciu metody [CKeyboardManager::SaveState](#savestate).  
  
 Jeśli nie określisz domyślnego okna głównego okna ramowego aplikacji będą używane.  
  
##  <a name="resetall"></a>  CKeyboardManager::ResetAll  
 Ponowne ładowanie tabel klucza skrótu z zasobów aplikacji.  
  
```  
void ResetAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja usuwa skróty przechowywane w `CKeyboardManager` wystąpienia. Następnie zostanie załadowana ponownie stan Menedżera klawiatury z zasobów aplikacji.  
  
##  <a name="savestate"></a>  CKeyboardManager::SaveState  
 Zapisuje skrót tabel klucza rejestru systemu Windows.  
  
```  
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszProfileName*  
 Ścieżka rejestru zapisywania `CKeyboardManager` stanu.  
  
 [in] *pDefaultFrame*  
 Wskaźnik do ramki okna, które staje się oknem domyślne.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli stan Menedżera klawiatury została zapisana pomyślnie, lub wpisz 0, w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *lpszProfileName* parametr jest `NULL`, ta metoda będzie zapisywać `CKeyboardManager` stanu do domyślnej lokalizacji podanej przez [CWinAppEx klasy](../../mfc/reference/cwinappex-class.md). Jeśli określisz lokalizacji można załadować danych później przy użyciu metody [CKeyboardManager::LoadState](#loadstate).  
  
 Jeśli nie określisz domyślnego okna głównego okna ramowego będzie używany jako domyślnego okna.  
  
##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators  
 Przedstawia wszystkie klawisze skrótu skojarzony z poleceń menu.  
  
```  
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,  
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bShowAll*  
 Jeśli `true`, wyświetlane są wszystkie klawisze skrótu. Jeśli `false`, zostanie wyświetlony tylko pierwszy klawisz skrótu.  
  
 [in] *lpszDelimiter*  
 Ciąg, aby wstawić między klawiszy skrótów. Tym ogranicznikiem nie ma znaczenia, jeśli tylko jeden klawisz skrótu jest wyświetlany.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie jeśli polecenie ma więcej niż jeden klawisz skrótu skojarzony z nim, tylko pierwszy klawisz skrótu będą wyświetlane. Ta funkcja umożliwia listę wszystkich skojarzonych z wszystkich poleceń klawiszy skrótów.  
  
 Klawisze skrótu będzie wyświetlane obok polecenia na pasku menu. Jeśli wyświetlane są wszystkie klawisze skrótu, ciąg udostępniane przez *lpszDelimiter* musi upłynąć klawiszy skrótów.  
  
##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper  
 Konwertuje znak na jego górnej rejestru.  
  
```  
static UINT TranslateCharToUpper(const UINT nChar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nChar*  
 Znak do konwersji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Znak, który jest górny rejestru parametru wejściowego.  
  
##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable  
 Aktualizuje tabeli klawiszy skrótów nowej tabeli klawiszy skrótów.  
  
```  
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    LPACCEL lpAccel,  
    int nSize,  
    CFrameWnd* pDefaultFrame = NULL);

 
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,  
    HACCEL hAccelNew,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pTemplate*  
 Wskaźnik do szablonu dokumentu.  
  
 [in] *lpAccel*  
 Wskaźnik do nowego klucza skrótu.  
  
 [in] *nSize*  
 Rozmiar nowej tabeli skrótów.  
  
 [in] *pDefaultFrame*  
 Wskaźnik do domyślnego ramki okna.  
  
 [in] *hAccelNew*  
 Dojście do nowej tabeli skrótów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby zamienić istniejącej tabeli skrótów nowe skróty klawiaturowe kilka obiektów okno ramowe. Funkcja odbiera szablonu dokumentu jako parametr, aby uzyskać dostęp do wszystkich obiektów okno ramowe podłączone do danego dokumentu szablonu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)   
 [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md)



