---
title: Klasa CMFCMaskedEdit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
dev_langs:
- C++
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0ada987b3226d901c3bf01236c2a593c2e36f51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcmaskededit-class"></a>Klasa CMFCMaskedEdit
`CMFCMaskedEdit` Klasa obsługuje formant zamaskowanej edycji, który sprawdza poprawność danych wejściowych użytkownika przed maski i wyświetla zweryfikowanych wyników na podstawie szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|Domyślny konstruktor.|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](#disablemask)|Wyłącza sprawdzanie poprawności danych wejściowych użytkownika.|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Określa, czy `GetWindowText` metoda pobiera tylko maskowanego znaków.|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicjuje zamaskowanej edycji.|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Określa, czy maskowana kontrolka edycji wybiera określonych grup danych wejściowych użytkownika lub wszystkich danych wejściowych użytkownika.|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Określa, czy tekst jest weryfikowana pod kątem tylko maskowane znaków lub dla całego maski.|  
|`CMFCMaskedEdit::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Pobiera zweryfikować tekst z maskowana kontrolka edycji.|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Określa ciąg prawidłowe znaki, które użytkownik może wprowadzić.|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Wyświetla monit o maskowana kontrolka edycji.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Wywoływane przez platformę, by sprawdzić poprawność określonego znaku względem odpowiedni znak maski.|  
  
## <a name="remarks"></a>Uwagi  
 Wykonaj poniższe kroki, aby użyć `CMFCMaskedEdit` kontroli w aplikacji:  
  
 1. Osadź `CMFCMaskedEdit` obiektu do klasy okna.  
  
 2. Wywołanie [CMFCMaskedEdit::EnableMask](#enablemask) metodę, aby określić maski.  
  
 3. Wywołanie [CMFCMaskedEdit::SetValidChars](#setvalidchars) metodę, aby określić listę prawidłowych znaków.  
  
 4. Wywołanie [CMFCMaskedEdit::SetWindowText](#setwindowtext) metodę, aby określić domyślny tekst formantu edycyjnego maskowanego.  
  
 5. Wywołanie [CMFCMaskedEdit::GetWindowText](#getwindowtext) metoda pobierania zweryfikowanych tekstu.  
  
 Jeśli co najmniej jedną metodę zainicjować maski, prawidłowe znaki i domyślny tekst nie zostanie wywołana, maskowana kontrolka edycji zachowuje się tak samo, jak działa kontrolki edycji standard.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak skonfigurować maski (na przykład numer telefonu) przy użyciu `EnableMask` metodę w celu utworzenia maski dla zamaskowanej edycji, `SetValidChars` metodę, aby określić parametry prawidłowe znaki, które użytkownik może wprowadzić i `SetWindowText` metodę w celu wyświetlenia monitu w zamaskowanej edycji. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmaskededit.h  
  
##  <a name="disablemask"></a>CMFCMaskedEdit::DisableMask  
 Wyłącza sprawdzanie poprawności danych wejściowych użytkownika.  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>Uwagi  
 Wyłączenie sprawdzania poprawności danych wejściowych użytkownika maskowana kontrolka edycji zachowuje się jak standardowy formantów edycji.  
  
##  <a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 Określa, czy `GetWindowText` metoda pobiera tylko maskowanego znaków.  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby określić, że [CMFCMaskedEdit::GetWindowText](#getwindowtext) metody pobierania tylko maskowane znaków. `FALSE` do określenia, że metoda pobieranie całego tekstu. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby umożliwić pobieranie maskowanego znaków. Następnie utwórz kontrolkę zamaskowanej edycji, która odpowiada numer telefonu, takich jak (425) 555-0187. Jeśli należy wywołać `GetWindowText` metoda zwraca "4255550187". Jeśli wyłączysz pobierania maskowanego znaków `GetWindowText` metoda zwraca tekst, który jest wyświetlany w formancie edycyjnym, na przykład "(425) 555-0187".  
  
##  <a name="enablemask"></a>CMFCMaskedEdit::EnableMask  
 Inicjuje zamaskowanej edycji.  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszMask`  
 Ciąg maski, który określa typ znaków, które mogą być wyświetlane na każdej pozycji w danych wejściowych użytkownika. Długość `lpszInputTemplate` i `lpszMask` ciągów parametrów muszą być takie same. W sekcji uwag więcej szczegółów na temat znaków maski.  
  
 [in]`lpszInputTemplate`  
 Ciąg szablonu maski, który określa, że literał znaków, które mogą występować na każdej pozycji w danych wejściowych użytkownika. Użyj znaku podkreślenia (_) jako symbol zastępczy znaków. Długość `lpszInputTemplate` i `lpszMask` ciągów parametrów muszą być takie same.  
  
 [in]`chMaskInputTemplate`  
 Domyślny znak platformę zastępuje każdy nieprawidłowy znak w danych wejściowych użytkownika. Wartością domyślną tego parametru jest znak podkreślenia (_).  
  
 [in]`lpszValid`  
 Ciąg, który zawiera zbiór prawidłowych znaków. `NULL`Wskazuje, czy wszystkie znaki są poprawne. Wartością domyślną tego parametru jest `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia utworzenie maskowana kontrolka edycji do maski. Klasa wyprowadzona z `CMFCMaskedEdit` klasy i zastąpić [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) metoda do użycia z własnego kodu podczas przetwarzania niestandardowej maski.  
  
 Następująca tabela zawiera listę znaków maski domyślnych:  
  
|Maski znaków|Definicja|  
|--------------------|----------------|  
|D|Cyfra.|  
|d|Cyfra lub spacja.|  
|+|Plus ("+"), minus ("-"), lub miejsca.|  
|C|Alfabetu.|  
|c|Literę alfabetu lub miejsca.|  
|ELEMENT|Znak alfanumeryczny.|  
|A|Znaki alfanumeryczne lub miejsca.|  
|*|Znak do druku.|  
  
##  <a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup  
 Określa, czy maskowana kontrolka edycji zezwala użytkownikowi na określonym grupom w danych wejściowych lub wszystkie dane wejściowe.  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby wybrać tylko grupy; `FALSE` aby zaznaczyć cały tekst. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja umożliwia określenie, czy maskowana kontrolka edycji zezwala użytkownikowi na wybranie według grupy lub całego tekstu.  
  
 Domyślnie zaznaczenie przez grupę jest włączone. W takim przypadku użytkownik może wybrać tylko prawidłowe znaki ciągłego grup.  
  
 Na przykład może użyć następujących maskowana kontrolka edycji można sprawdzić poprawności numeru telefonu:  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 Jeśli włączono wybór przez grupę, użytkownik może pobrać tylko "425", "555" lub "0187" ciąg grup. Po wyłączeniu wybranej grupy użytkownika mogą pobierać całego tekstu numer telefonu: "(425) 555-0187".  
  
##  <a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 Określa, czy tekst jest zweryfikowany względem maskowanego znaki lub względem całego maski.  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`do weryfikacji użytkownika porównanie danych wejściowych tylko maskowane znaków. `FALSE` na potrzeby sprawdzania poprawności całej maski. Wartość domyślna to `TRUE`.  
  
##  <a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText  
 Pobiera zweryfikować tekst z maskowana kontrolka edycji.  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`lpszStringBuf`  
 Wskaźnik do buforu, który odbiera tekst w formancie edycji.  
  
 [in]`nMaxCount`  
 Maksymalna liczba znaków do odbierania.  
  
 [out]`rstrString`  
 Odwołanie do obiektu ciąg, który odbiera tekst w formancie edycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy przeciążenie metody zwraca liczbę bajtów ciąg, który jest kopiowany do `lpszStringBuf` buforu parametru; 0, jeśli kontrolka zamaskowanej edycji nie ma tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda kopiuje tekst z maskowana kontrolka edycji do `lpszStringBuf` buforu lub `rstrString` ciągu.  
  
 Ta metoda ponownie definiuje [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).  
  
##  <a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar  
 Wywoływane przez platformę, by sprawdzić poprawność określonego znaku względem odpowiedni znak maski.  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`chChar`  
 Znak do sprawdzenia poprawności.  
  
 [in]`chMaskChar`  
 Odpowiedni znak z ciągu maski.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli `chChar` parametr jest typu znaków dozwoloną przez `chMaskChar` parametru; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę do sprawdzania poprawności wprowadzania znaków samodzielnie. Aby uzyskać więcej informacji na temat znaków maski, zobacz [CMFCMaskedEdit::EnableMask](#enablemask) metody.  
  
##  <a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars  
 Określa ciąg prawidłowe znaki, które użytkownik może wprowadzić.  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszValid`  
 Ciąg, który zawiera zbiór prawidłowych znaków wejściowego. `NULL`oznacza, że wszystkie znaki są poprawne. Wartością domyślną tego parametru jest `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby zdefiniować listę prawidłowych znaków. Jeśli znak wejściowy nie jest na liście, maskowana kontrolka edycji nie akceptuje on.  
  
 Poniższy przykład kodu akceptuje tylko cyfry szesnastkowe.  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText  
 Wyświetla monit o maskowana kontrolka edycji.  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszString`  
 Wskazuje ciąg zerem, który będzie używany jako wiersz.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia tekst formantu.  
  
 Ta metoda ponownie definiuje [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)
