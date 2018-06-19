---
title: Klasa CD2DBitmap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b92587d6cad3004c87ee6aee4716888d09c1270a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354285"
---
# <a name="cd2dbitmap-class"></a>Klasa CD2DBitmap
Otoka dla ID2D1Bitmap.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DBitmap : public CD2DResource;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Przeciążone. Tworzy obiekt CD2DBitmap z HBITMAP.|  
|[CD2DBitmap:: ~ CD2DBitmap](#_dtorcd2dbitmap)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D mapy bitowej.|  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Przeciążone. Tworzy obiekt CD2DBitmap.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmap::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Kopiuje określony region z Podana mapa bitowa do bieżącego mapy bitowej|  
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Kopiuje określony region z pamięci do bieżącego mapy bitowej|  
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Kopie określonego regionu z określonym elementem docelowym renderowania do bieżącego mapy bitowej|  
|[CD2DBitmap::Create](#create)|Tworzy CD2DBitmap. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmap::Destroy](#destroy)|Niszczy obiektu CD2DBitmap. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DBitmap::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DBitmap::Get](#get)|Zwraca interfejs ID2D1Bitmap|  
|[CD2DBitmap::GetDPI](#getdpi)|Zwraca punktów na cal (DPI) mapy bitowej|  
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Pobiera tryb format i alfa pikseli mapy bitowej|  
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Zwraca rozmiar w jednostki zależne od urządzenia (w pikselach), mapy bitowej|  
|[CD2DBitmap::GetSize](#getsize)|Zwraca rozmiar w pikselach niezależnych od urządzenia (DIP) mapy bitowej|  
|[CD2DBitmap::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmap::CommonInit](#commoninit)|Inicjuje obiekt|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmap::operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Zwraca interfejs ID2D1Bitmap|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|Wartość TRUE, jeśli należy zniszczyć m_hBmpSrc; w przeciwnym razie wartość FALSE.|  
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Dojście do źródła mapy bitowej.|  
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Typ zasobu.|  
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Przechowuje wskaźnika do obiektu ID2D1Bitmap.|  
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Bitmap — rozmiar docelowy.|  
|[CD2DBitmap::m_strPath](#m_strpath)|Ścieżka pliku Botmap.|  
|[CD2DBitmap::m_uiResID](#m_uiresid)|Identyfikator zasobu mapy bitowej.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DBitmap`
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dbitmap"></a>  CD2DBitmap:: ~ CD2DBitmap  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu D2D mapy bitowej.  
  
```  
virtual ~CD2DBitmap();
```  
  
##  <a name="attach"></a>  CD2DBitmap::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1Bitmap* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dbitmap"></a>  CD2DBitmap::CD2DBitmap  
 Tworzy obiekt CD2DBitmap z zasobu.  
  
```  
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszPath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    HBITMAP hbmpSrc,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
 `uiResID`  
 Identyfikatora zasobu zasobu.  
  
 `lpszType`  
 Wskaźnik do zerem ciąg, który zawiera typ zasobu.  
  
 `sizeDest`  
 Rozmiar docelowego mapy bitowej.  
  
 `bAutoDestroy`  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
 `lpszPath`  
 Wskaźnik do zerem ciąg, który zawiera nazwę pliku.  
  
 `hbmpSrc`  
 Dojście do mapy bitowej.  
  
##  <a name="commoninit"></a>  CD2DBitmap::CommonInit  
 Inicjuje obiekt  
  
```  
void CommonInit();
```  
  
##  <a name="copyfrombitmap"></a>  CD2DBitmap::CopyFromBitmap  
 Kopiuje określony region z Podana mapa bitowa do bieżącego mapy bitowej  
  
```  
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Mapy bitowej do skopiowania  
  
 `destPoint`  
 W bieżącym mapy bitowej lewego górnego rogu obszaru, do którego region określony przez srcRect jest kopiowana  
  
 `srcRect`  
 Obszar mapy bitowej do skopiowania  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="copyfrommemory"></a>  CD2DBitmap::CopyFromMemory  
 Kopiuje określony region z pamięci do bieżącego mapy bitowej  
  
```  
HRESULT CopyFromMemory(
    const void* srcData,  
    UINT32 pitch,  
    const CD2DRectU* destRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `srcData`  
 Dane do skopiowania.  
  
 `pitch`  
 Krok lub wysokość mapy bitowej źródła przechowywane w srcData. Krok to liczba bajtów scanline (jeden wiersz pikseli w pamięci). Z następującej formuły można obliczyć krok: szerokość piksela * bajtów na piksel + uzupełnienia pamięci  
  
 `destRect`  
 W bieżącym mapy bitowej lewego górnego rogu obszaru, do którego region określony przez srcRect jest kopiowana  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="copyfromrendertarget"></a>  CD2DBitmap::CopyFromRenderTarget  
 Kopie określonego regionu z określonym elementem docelowym renderowania do bieżącego mapy bitowej  
  
```  
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Zawierający regionie można skopiować obiektu docelowego renderowania  
  
 `destPoint`  
 W bieżącym mapy bitowej lewego górnego rogu obszaru, do którego region określony przez srcRect jest kopiowana  
  
 `srcRect`  
 Obszar obiektu docelowego renderowania Aby skopiować  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="create"></a>  CD2DBitmap::Create  
 Tworzy CD2DBitmap.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>  CD2DBitmap::Destroy  
 Niszczy obiektu CD2DBitmap.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DBitmap::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1Bitmap* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>  CD2DBitmap::Get  
 Zwraca interfejs ID2D1Bitmap  
  
```  
ID2D1Bitmap* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Bitmap lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="getdpi"></a>  CD2DBitmap::GetDPI  
 Zwraca punktów na cal (DPI) mapy bitowej  
  
```  
CD2DSizeF GetDPI() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Poziome i pionowe DPI mapy bitowej.  
  
##  <a name="getpixelformat"></a>  CD2DBitmap::GetPixelFormat  
 Pobiera tryb format i alfa pikseli mapy bitowej  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Piksel format i alfa tryb mapy bitowej.  
  
##  <a name="getpixelsize"></a>  CD2DBitmap::GetPixelSize  
 Zwraca rozmiar w jednostki zależne od urządzenia (w pikselach), mapy bitowej  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar w pikselach, mapy bitowej.  
  
##  <a name="getsize"></a>  CD2DBitmap::GetSize  
 Zwraca rozmiar w pikselach niezależnych od urządzenia (DIP) mapy bitowej  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar w pikselach DIP mapy bitowej.  
  
##  <a name="isvalid"></a>  CD2DBitmap::IsValid  
 Sprawdzanie poprawności zasobów  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_bautodestroyhbmp"></a>  CD2DBitmap::m_bAutoDestroyHBMP  
 Wartość TRUE, jeśli należy zniszczyć m_hBmpSrc; w przeciwnym razie wartość FALSE.  
  
```  
BOOL m_bAutoDestroyHBMP;  
```  
  
##  <a name="m_hbmpsrc"></a>  CD2DBitmap::m_hBmpSrc  
 Dojście do źródła mapy bitowej.  
  
```  
HBITMAP m_hBmpSrc;  
```  
  
##  <a name="m_lpsztype"></a>  CD2DBitmap::m_lpszType  
 Typ zasobu.  
  
```  
LPCTSTR m_lpszType;  
```  
  
##  <a name="m_pbitmap"></a>  CD2DBitmap::m_pBitmap  
 Przechowuje wskaźnika do obiektu ID2D1Bitmap.  
  
```  
ID2D1Bitmap* m_pBitmap;  
```  
  
##  <a name="m_sizedest"></a>  CD2DBitmap::m_sizeDest  
 Bitmap — rozmiar docelowy.  
  
```  
CD2DSizeU m_sizeDest;  
```  
  
##  <a name="m_strpath"></a>  CD2DBitmap::m_strPath  
 Ścieżka pliku Botmap.  
  
```  
CString m_strPath;  
```  
  
##  <a name="m_uiresid"></a>  CD2DBitmap::m_uiResID  
 Identyfikator zasobu mapy bitowej.  
  
```  
UINT m_uiResID;  
```  
  
##  <a name="operator_id2d1bitmap_star"></a>  CD2DBitmap::operator ID2D1Bitmap *  
 Zwraca interfejs ID2D1Bitmap  
  
```  
operator ID2D1Bitmap*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Bitmap lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
