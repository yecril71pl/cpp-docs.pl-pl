---
title: Klasa CBitmapButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
dev_langs: C++
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 619ddd7805207f14bb44ed52d148f53e3aa79e57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cbitmapbutton-class"></a>Klasa CBitmapButton
Tworzy łącznik formanty etykietą map bitowych obrazów zamiast tekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CBitmapButton : public CButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Konstruuje `CBitmapButton` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBitmapButton::AutoLoad](#autoload)|Kojarzy przycisk w oknie dialogowym z obiektu `CBitmapButton` klasy ładuje bitmap(s) według nazwy i rozmiar przycisk, aby dopasować mapy bitowej.|  
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicjuje obiekt ładowania co najmniej jeden zasób o nazwie mapy bitowej z pliku zasobów aplikacji i dołączanie do obiektu map bitowych.|  
|[CBitmapButton::SizeToContent](#sizetocontent)|Rozmiary przycisk, aby pomieścić mapy bitowej.|  
  
## <a name="remarks"></a>Uwagi  
 `CBitmapButton`obiekty zawierają maksymalnie cztery mapy bitowe, zawierające obrazy do innych stanów przycisku można założyć: się (lub normalna), dół (lub wybranych), fokus i wyłączone. Tylko pierwszy mapy bitowej jest wymagana. inne są opcjonalne.  
  
 Obrazy dla przycisków mapy bitowej obejmują obramowania wokół obrazu, a także samego obrazu. Obramowanie zwykle odgrywa rolę podczas wyświetlania stanu przycisku. Na przykład mapy bitowej dla stanu ukierunkowanych zazwyczaj jest podobny do konfigurowania stanu, ale wstawki kreskowane prostokąta, obramowanie lub grubości linii ciągłej na granicy. Mapa bitowa dla osób niepełnosprawnych stanu zwykle podobny do jednego dla stan up, lecz jest niższe kontrastu (np. menu na wygaszone lub wyszarzonymi polami wyboru).  
  
 Te mapy bitowe mogą być o dowolnym rozmiarze, ale wszystkie są traktowane, tak jakby były to taki sam rozmiar jak mapa bitowa w górę stanu.  
  
 Różne aplikacje wymagać różnych kombinacji map bitowych:  
  
|W górę|W dół|Fokus|Wyłączone|Aplikacja|  
|--------|----------|-------------|--------------|-----------------|  
|×||||Mapy bitowej|  
|×|×|||Przycisk bez **ws_tabstop —** stylu|  
|×|×|×|×|Przycisk okna dialogowego z wszystkich stanów|  
|×|×|×||Przycisk okna dialogowego z **ws_tabstop —** stylu|  
  
 Podczas tworzenia kontrolkę przycisku mapy bitowej należy skonfigurować **bs_ownerdraw —** stylu, aby określić, czy przycisk jest rysowane przez właściciela. Powoduje to, że system Windows do wysyłania `WM_MEASUREITEM` i `WM_DRAWITEM` wiadomości dla przycisku; ramach obsługi tych wiadomości i zarządza wygląd przycisku dla Ciebie.  
  
### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Aby utworzyć kontrolkę przycisku mapy bitowej w obszaru klienckiego okna  
  
1.  Tworzenie obrazów mapy bitowej 1 do 4 dla przycisku.  
  
2.  Utworzyć [CBitmapButton](#cbitmapbutton) obiektu.  
  
3.  Wywołanie [Utwórz](../../mfc/reference/cbutton-class.md#create) funkcja Utwórz kontrolkę przycisku systemu Windows i dołączenie go do `CBitmapButton` obiektu.  
  
4.  Wywołanie [LoadBitmaps](#loadbitmaps) funkcji członkowskiej załadować zasoby mapy bitowej po przycisk mapy bitowej jest tworzony.  
  
### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Aby uwzględnić kontrolkę przycisku mapy bitowej w oknie dialogowym  
  
1.  Tworzenie obrazów mapy bitowej 1 do 4 dla przycisku.  
  
2.  Tworzenie szablonu okna dialogowego z przyciskiem rysowania przez właściciela odległości przycisk mapy bitowej. Rozmiar przycisku w szablonie nie ma znaczenia.  
  
3.  Takie jak ustawienie przycisku na wartość " **MYIMAGE**" i zdefiniuj symbol dla przycisku, takich jak **IDC_MYIMAGE**.  
  
4.  W aplikacji skrypt zasobu Nadaj każdej obrazy utworzone dla przycisku wykonane przez dodanie jednej litery "U", "D", "F", identyfikator lub "X" (na górę, dół, fokus i wyłączony) na ciąg używany dla podpisu przycisku w kroku 3. Dla podpisu przycisku " **MYIMAGE**," na przykład, będzie identyfikatorów " **MYIMAGEU**," " **MYIMAGED**," " **MYIMAGEF**," i " **MYIMAGEX**. " Możesz **musi** Podaj identyfikator użytkownika map bitowych w podwójny cudzysłów. W przeciwnym razie edytora zasobów przypisze całkowitą zasobu i MFC zakończy się niepowodzeniem podczas ładowania obrazu.  
  
5.  W aplikacji klasy okien dialogowych (pochodną `CDialog`), Dodaj `CBitmapButton` obiektu elementu członkowskiego.  
  
6.  W `CDialog` obiektu [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) wywołaniu procedury, `CBitmapButton` obiektu [automatyczne ładowanie](#autoload) działanie, używając jako parametry Identyfikatora formantu przycisku i `CDialog` obiektu **to** wskaźnika.  
  
 Jeśli chcesz obsługi komunikatów powiadomień systemu Windows, takich jak **BN_CLICKED**, wysłanych przez kontrolkę przycisku mapy bitowej do elementu nadrzędnego (zwykle klasą pochodną **cdialog —)**, Dodaj do `CDialog`-pochodnych Obiekt mapy komunikatów wpisu i program obsługi komunikatów funkcją członkowską dla każdego komunikatu. Powiadomienia wysyłane przez `CBitmapButton` obiektu są takie same jak wysyłane przez [CButton](../../mfc/reference/cbutton-class.md) obiektu.  
  
 Klasa [ctoolbar —](../../mfc/reference/ctoolbar-class.md) mają inne podejście do przycisków mapy bitowej.  
  
 Aby uzyskać więcej informacji na temat `CBitmapButton`, zobacz [formanty](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="autoload"></a>CBitmapButton::AutoLoad  
 Kojarzy przycisk w oknie dialogowym z obiektu `CBitmapButton` klasy ładuje bitmap(s) według nazwy i rozmiar przycisk, aby dopasować mapy bitowej.  
  
```  
BOOL AutoLoad(
    UINT nID,  
    CWnd* pParent);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identyfikator formantu przycisku.  
  
 `pParent`  
 Wskaźnik do obiektu, który jest właścicielem przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `AutoLoad` funkcji, aby zainicjować przycisk rysowania przez właściciela, w oknie dialogowym jako przycisk mapy bitowej. Instrukcje dotyczące używania tej funkcji znajdują się w uwagi dla `CBitmapButton` klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]  
  
##  <a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton  
 Tworzy `CBitmapButton` obiektu.  
  
```  
CBitmapButton();
```  
  
### <a name="remarks"></a>Uwagi  
 Po utworzeniu C++ `CBitmapButton` obiekt, należy wywołać [CButton::Create](../../mfc/reference/cbutton-class.md#create) Utwórz kontrolkę przycisku systemu Windows i dołączenie go do `CBitmapButton` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]  
  
##  <a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps  
 Użyj tej funkcji, jeśli chcesz załadować bitmapy zidentyfikowane przy użyciu ich nazw zasobów lub numerów Identyfikacyjnych lub gdy nie można użyć `AutoLoad` działać, ponieważ na przykład tworzysz przycisk mapy bitowej, który nie jest częścią okno dialogowe.  
  
```  
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,  
    LPCTSTR lpszBitmapResourceSel = NULL,  
    LPCTSTR lpszBitmapResourceFocus = NULL,  
    LPCTSTR lpszBitmapResourceDisabled = NULL);

 
BOOL LoadBitmaps(
    UINT nIDBitmapResource,  
    UINT nIDBitmapResourceSel = 0,  
    UINT nIDBitmapResourceFocus = 0,  
    UINT nIDBitmapResourceDisabled = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszBitmapResource*  
 Wskazuje zerem ciągu zawierającego nazwę mapy bitowej do normalnego przycisku Mapa bitowa lub "informacje" o stanie. Wymagany.  
  
 *lpszBitmapResourceSel*  
 Punkty zerem ciąg zawierający nazwę mapy bitowej dla przycisku mapy bitowej na wybranych lub w "stanie dół". Może być **NULL**.  
  
 *lpszBitmapResourceFocus*  
 Wskazuje ciąg zakończony zerem, która zawiera nazwę mapy bitowej dla przycisku mapy bitowej fokus stanu. Może być **NULL**.  
  
 *lpszBitmapResourceDisabled*  
 Wskazuje zerem ciągu zawierającego nazwę mapy bitowej dla przycisku mapy bitowej stan wyłączenia. Może być **NULL**.  
  
 *nIDBitmapResource*  
 Określa identyfikator zasobu zasobu mapy bitowej do normalnego przycisku Mapa bitowa lub "informacje" o stanie. Wymagany.  
  
 *nIDBitmapResourceSel*  
 Określa identyfikator zasobu zasobu mapy bitowej przez wybrany przycisk mapa bitowa lub "w dół" stan. Może być równa 0.  
  
 *nIDBitmapResourceFocus*  
 Określa zasób identyfikator zasobu mapy bitowej dla stanu ukierunkowanych przycisk mapy bitowej. Może być równa 0.  
  
 *nIDBitmapResourceDisabled*  
 Określa identyfikator zasobu mapy bitowej zasobu w stanie wyłączenia przycisk mapy bitowej. Może być równa 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]  
  
##  <a name="sizetocontent"></a>CBitmapButton::SizeToContent  
 Wywołanie tej funkcji, aby zmienić rozmiar przycisku mapy bitowej do rozmiaru mapy bitowej.  
  
```  
void SizeToContent();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLTEST](../../visual-cpp-samples.md)   
 [Klasa CButton](../../mfc/reference/cbutton-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)

