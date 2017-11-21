---
title: Klasa CColorDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
dev_langs: C++
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 329474d7d2212d621bdf263021a86d170118f1b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccolordialog-class"></a>Klasa CColorDialog
Umożliwia włączenie okno dialogowe wybór kolorów do aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](#ccolordialog)|Konstruuje `CColorDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CColorDialog::DoModal](#domodal)|Wyświetla okno dialogowe kolorów i umożliwia użytkownikowi dokonanie wyboru.|  
|[CColorDialog::GetColor](#getcolor)|Zwraca **COLORREF** struktury zawierającej wartości kolorów.|  
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Pobiera kolory niestandardowe utworzone przez użytkownika.|  
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Wymusza bieżącego zaznaczenia kolorów określonego koloru.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](#oncolorok)|Należy przesłonić, aby zweryfikować kolor wprowadzone w oknie dialogowym.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CColorDialog::m_cc](#m_cc)|Struktura używane do dostosowywania ustawień w oknie dialogowym.|  
  
## <a name="remarks"></a>Uwagi  
 A `CColorDialog` obiektu to okno dialogowe z listą kolorów, które są zdefiniowane dla systemu wyświetlania. Użytkownika można wybrać lub utworzyć określonego koloru z listy, która jest następnie zgłaszana z powrotem do aplikacji po zamknięciu okna dialogowego.  
  
 Aby utworzyć `CColorDialog` obiektów, użyj dostarczonego konstruktora lub pochodzić nową klasę i używanie własnych niestandardowych konstruktora.  
  
 Gdy okno dialogowe zostały utworzone, możesz ustawić lub zmodyfikować wartości w [m_cc](#m_cc) struktury zainicjować wartości formantów okna dialogowego. `m_cc` Struktura jest typu [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830).  
  
 Po inicjowanie formantów okna dialogowego, należy wywołać `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na wybranie koloru. `DoModal`Zwraca określonego przez użytkownika albo OK w oknie dialogowym ( **IDOK**), lub Anuluj ( **IDCANCEL**) przycisku.  
  
 Jeśli `DoModal` zwraca **IDOK**, można użyć jednej z `CColorDialog`w funkcji elementów członkowskich do pobrania informacji o danych wejściowych przez użytkownika.  
  
 Można użyć Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkcji, aby ustalić, czy wystąpił błąd podczas inicjowania okna dialogowego i aby dowiedzieć się więcej o tym błędzie.  
  
 `CColorDialog`zależy od pliku COMMDLG. Plik DLL, która jest dostarczana z systemem Windows w wersji 3.1 lub nowszej.  
  
 Aby dostosować okno dialogowe, pochodzi z klasy `CColorDialog`, podaj szablon niestandardowe okno dialogowe i dodać mapy komunikatów do przetwarzania komunikatów powiadomień od formantów rozszerzonego. Komunikaty nieprzetworzone powinny zostać przekazane do klasy podstawowej.  
  
 Dostosowywanie funkcji punktów zaczepienia nie jest wymagane.  
  
> [!NOTE]
>  Na niektóre instalacje `CColorDialog` obiektu nie będą wyświetlane na szarym tle użycie platformę dokonanie innych `CDialog` szary obiektów.  
  
 Aby uzyskać więcej informacji na temat używania `CColorDialog`, zobacz [klasy wspólnych okien dialogowych](../../mfc/common-dialog-classes.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="ccolordialog"></a>CColorDialog::CColorDialog  
 Konstruuje `CColorDialog` obiektu.  
  
```  
CColorDialog(
    COLORREF clrInit = 0,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *clrInit*  
 Domyślny wybór kolorów. Jeśli wartość nie zostanie określona, wartością domyślną jest RGB(0,0,0) (czarny).  
  
 `dwFlags`  
 Zestaw flag, które dostosowanie funkcji i wyglądu w oknie dialogowym. Aby uzyskać więcej informacji, zobacz [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830) struktury w zestawie Windows SDK.  
  
 `pParentWnd`  
 Wskaźnik do okna nadrzędnego lub właściciela okna dialogowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CColorDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe kolorów wspólne systemu Windows i Zezwalaj użytkownikowi na wybranie koloru.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **IDOK** lub **IDCANCEL**. Jeśli **IDCANCEL** jest zwracany, wywołanie systemu Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkcji, aby ustalić, czy wystąpił błąd.  
  
 **IDOK** i **IDCANCEL** są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różne opcje Okno dialogowe kolorów przez ustawienie członkami [m_cc](#m_cc) struktury, należy to zrobić przed wywołaniem `DoModal` , ale po konstruowania obiektu okno dialogowe.  
  
 Po wywołaniu `DoModal`, innego członka można wywołać funkcji można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CColorDialog::CColorDialog](#ccolordialog).  
  
##  <a name="getcolor"></a>CColorDialog::GetColor  
 Wywołanie tej funkcji po wywołaniu `DoModal` można pobrać informacji o kolor wybrany przez użytkownika.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości, która zawiera dane RGB kolor wybrany w oknie dialogowym koloru.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]  
  
##  <a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors  
 `CColorDialog`obiekty zezwolić użytkownikowi, oprócz możliwości wyboru kolory, aby zdefiniować do 16 kolorów niestandardowych.  
  
```  
static COLORREF* PASCAL GetSavedCustomColors();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do tablicy wartości kolorów RGB 16 przechowuje kolory niestandardowe utworzone przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 `GetSavedCustomColors` Funkcji członkowskiej zapewnia dostęp do tych kolorów. Kolorów te mogą zostać pobrane po [DoModal](#domodal) zwraca **IDOK**.  
  
 16 wartości RGB w tablicy zwracane jest ustawiana na RGB(255,255,255) (biały). Kolory niestandardowe wybierany przez użytkownika są zapisywane tylko między wywołań — okno dialogowe w aplikacji. Jeśli chcesz zapisać te kolory wywołań aplikacji, musisz zapisać je w inny sposób, takie jak podczas inicjowania (. Plik INI).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]  
  
##  <a name="m_cc"></a>CColorDialog::m_cc  
 Struktura typu [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830), której członkowie przechowywania właściwości i wartości w oknie dialogowym.  
  
```  
CHOOSECOLOR m_cc;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania `CColorDialog` obiektu, można użyć `m_cc` można ustawić różne aspekty okna dialogowego przed wywołaniem [DoModal](#domodal) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]  
  
##  <a name="oncolorok"></a>CColorDialog::OnColorOK  
 Należy przesłonić, aby zweryfikować kolor wprowadzone w oknie dialogowym.  
  
```  
virtual BOOL OnColorOK();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli okno dialogowe nie powinny być odrzucane; w przeciwnym razie 0, aby zaakceptować kolor, który został wprowadzony.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję tylko wtedy, gdy chcesz zapewnić niestandardowego sprawdzania poprawności koloru wybranego przez użytkownika w oknie dialogowym koloru.  
  
 Użytkownik może wybrać kolor przez jedną z następujących dwóch metod:  
  
-   Klikając przycisk kolor w palecie kolorów. Wartości RGB wybranego koloru następnie są uwzględniane w odpowiednich polach edycji RGB.  
  
-   Wprowadzanie wartości RGB pola edycji  
  
 Zastępowanie `OnColorOK` umożliwia odrzucanie kolor wprowadzonych przez użytkownika w typowych okno dialogowe kolorów jakiegokolwiek powodu specyficzne dla aplikacji.  
  
 Zwykle nie trzeba używać tej funkcji, ponieważ framework zapewnia domyślnego procesu sprawdzania poprawności kolorów i wyświetla komunikat, jeśli zostanie wprowadzony nieprawidłowy kolor.  
  
 Możesz wywołać [SetCurrentColor](#setcurrentcolor) z poziomu `OnColorOK` wymusić wybór kolorów. Raz `OnColorOK` zostały uruchamiany (oznacza to, że użytkownik klika polecenie **OK** aby zaakceptować zmianę koloru), można wywołać [GetColor](#getcolor) można pobrać wartości RGB nowego koloru.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]  
  
##  <a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor  
 Wywołanie tej funkcji po wywołaniu `DoModal` wymusić bieżącego zaznaczenia koloru wartość koloru określone w `clr`.  
  
```  
void SetCurrentColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 Wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana z wewnątrz obsługi wiadomości lub `OnColorOK`. Okno dialogowe zostanie automatycznie zaktualizowane wybór użytkownika na podstawie wartości z `clr` parametru.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CColorDialog::OnColorOK](#oncolorok).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Przykładowe MFC DRAWCLI](../../visual-cpp-samples.md)   
 [Klasa CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)

