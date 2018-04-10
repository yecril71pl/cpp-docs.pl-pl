---
title: Klasa CStrBufT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8df7f6c1dbd9987a9f83ed5b33a4c97fd90fec7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cstrbuft-class"></a>Klasa CStrBufT
Ta klasa udostępnia Oczyszczanie automatyczne zasobów dla `GetBuffer` i `ReleaseBuffer` wywołuje na istniejącym `CStringT` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename TCharType>
class CStrBufT
```  
  
#### <a name="parameters"></a>Parametry  
 *TCharType*  
 Typ znakowy `CStrBufT` klasy. Może to być jedna z następujących czynności:  
  
- `char`(dla ciągów znaków ANSI)  
  
- `wchar_t`(dla ciągów znaków Unicode)  
  
- **Tchar —** (dla ciągów znaków ANSI jak również Unicode)  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`PCXSTR`|Wskaźnik ze stałym ciągiem.|  
|`PXSTR`|Wskaźnik do ciągu.|  
|`StringType`|Typu ciąg, którego buforu się manipulować specjalizacji szablonu klasy.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](#cstrbuft)|Konstruktor obiektu buforu ciągu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStrBufT::SetLength](#setlength)|Ustawia bufor znaków ciągu skojarzonego obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Pobiera **const** wskaźnika do buforu znaków ciągu skojarzonego obiektu.|  
|[CStrBufT::operator PXSTR](#operator_pxstr)|Pobiera wskaźnik do buforu znaków ciągu skojarzonego obiektu.|  
  
### <a name="public-constants"></a>Publiczny — stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStrBufT::AUTO_LENGTH](#auto_length)|Automatycznie określić nowe długość ciągu w wersji.|  
|[CStrBufT::SET_LENGTH](#set_length)|Ustawianie długości ciągu obiektu w momencie GetBuffer|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest używana jako klasa otoki dla zastępczych wywołaniach [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), lub [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) i `ReleaseBuffer`.  
  
 Przeznaczony głównie jako klasę Pomocnika `CStrBufT` oferują wygodny sposób dla deweloperów do pracy z buforu znak z obiektem ciągu, nie martwiąc się o tym, jak i kiedy wywołać metodę `ReleaseBuffer`. Jest to możliwe, ponieważ obiekt otoki odbywa się poza zakresem naturalnie w przypadku wyjątku lub wiele ścieżek kodu istniejących; powoduje jego destruktora zwolnienia zasobu ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpstr.h  
  
##  <a name="auto_length"></a>CStrBufT::AUTO_LENGTH  
 Automatycznie określić nowe długość ciągu w wersji.  
  
```
static const DWORD AUTO_LENGTH = 0x01;
```  
  
### <a name="remarks"></a>Uwagi  
 Automatycznie określić nowe długość ciągu w wersji. Ciąg musi być zakończony zerem.  
  
##  <a name="cstrbuft"></a>CStrBufT::CStrBufT  
 Tworzy obiekt buforu.  
  
```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Obiekt ciągu skojarzonego z buforu. Zazwyczaj dewelopera użyje wstępnie zdefiniowane elementy TypeDef z **CStrBuf** ( **tchar —** wariant), **CStrBufA** ( `char` wariant) i **CStrBufW**  ( `wchar_t` wariant).  
  
 *nMinLength*  
 Minimalna długość buforu znaków.  
  
 `dwFlags`  
 Określa, czy długość ciągu jest ustalany automatycznie. Może to być jedna z następujących czynności:  
  
- **AUTO_LENGTH** długość ciągu jest automatycznie ustalić, kiedy [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) jest wywoływana. Ciąg musi być zakończony zerem. Wartość domyślna.  
  
- **SET_LENGTH** długość ciągu jest ustawiana podczas [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) jest wywoływana.  
  
### <a name="remarks"></a>Uwagi  
 Utworzenie buforu ciągu dla obiekt ciągu skojarzone. Podczas konstruowania [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) lub [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) jest wywoływana.  
  
 Należy pamiętać, że Konstruktor kopiujący jest `private`.  
  
##  <a name="operator_pcxstr"></a>CStrBufT::operator PCXSTR  
 Bezpośredni dostęp do znaków przechowywanych w obiekcie skojarzone ciągu jako ciąg w stylu języka C.  
  
```  
operator PCXSTR() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Znak wskaźnikiem do danych ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji do zwraca wskaźnik do buforu znak z obiektem ciągu. Nie można zmienić zawartość z obiektem ciągu z ten wskaźnik.  
  
##  <a name="operator_pxstr"></a>CStrBufT::operator PXSTR  
 Bezpośredni dostęp do znaków przechowywanych w obiekcie skojarzone ciągu jako ciąg w stylu języka C.  
  
```
operator PXSTR() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Znak wskaźnikiem do danych ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji do zwraca wskaźnik do buforu znak z obiektem ciągu. Deweloper może zmienić zawartość z obiektem ciągu z ten wskaźnik.  
  
##  <a name="pcxstr"></a>CStrBufT::PCXSTR  
 Wskaźnik ze stałym ciągiem.  
  
```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```  
  
##  <a name="pxstr"></a>CStrBufT::PXSTR  
 Wskaźnik do ciągu.  
  
```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```  
  
##  <a name="set_length"></a>CStrBufT::SET_LENGTH  
 Ustawianie długości z obiektem ciągu w `GetBuffer` czasu.  
  
```
static const DWORD SET_LENGTH = 0x02;
```  
  
### <a name="remarks"></a>Uwagi  
 Ustawianie długości z obiektem ciągu w czasie GetBuffer.  
  
 Określa, czy [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) są wywoływane, gdy jest tworzony obiekt buforu ciągu.  
  
##  <a name="setlength"></a>CStrBufT::SetLength  
 Ustawia długość buforu znaków.  
  
```
void SetLength(int nLength);
```  
  
### <a name="parameters"></a>Parametry  
 `nLength`  
 Nowe długość buforu znak z obiektem ciągu.  
  
> [!NOTE]
>  Musi być mniejsza niż długość buforu minimalna określona w Konstruktorze `CStrBufT`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby ustawić długość ciągu reprezentowanych przez obiekt buforu.  
  
##  <a name="stringtype"></a>CStrBufT::StringType  
 Typu ciąg, którego buforu się manipulować specjalizacji szablonu klasy.  
  
```
typedef CSimpleStringT<TCharType> StringType;
```  
  
### <a name="remarks"></a>Uwagi  
 **TCharType** jest typem znak używany do specjalizować szablonu klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)


