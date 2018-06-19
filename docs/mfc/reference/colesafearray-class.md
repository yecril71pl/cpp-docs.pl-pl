---
title: Klasa COleSafeArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
dev_langs:
- C++
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e21cecc00c9aab170c79247bced635783541be48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376880"
---
# <a name="colesafearray-class"></a>Klasa COleSafeArray
Klasa do pracy z tablicami dowolnego typu i wymiaru.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleSafeArray : public tagVARIANT  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleSafeArray::COleSafeArray](#colesafearray)|Konstruuje `COleSafeArray` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleSafeArray::AccessData](#accessdata)|Pobiera wskaźnik do tablicy danych.|  
|[COleSafeArray::AllocData](#allocdata)|Przydziela pamięć dla tablicy.|  
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Przydziela pamięć dla deskryptora bezpiecznej tablicy.|  
|[COleSafeArray::Attach](#attach)|Zapewnia kontrolę istniejącej **VARIANT** tablicy do `COleSafeArray` obiektu.|  
|[COleSafeArray::Clear](#clear)|Zwalnia wszystkie dane w odpowiadającego **VARIANT**.|  
|[COleSafeArray::Copy](#copy)|Tworzy kopię istniejącej tablicy.|  
|[COleSafeArray::Create](#create)|Tworzy bezpiecznej tablicy.|  
|[COleSafeArray::CreateOneDim](#createonedim)|Tworzy jednowymiarowa `COleSafeArray` obiektu.|  
|[COleSafeArray::Destroy](#destroy)|Niszczy istniejącej tablicy.|  
|[COleSafeArray::DestroyData](#destroydata)|Niszczy dane w bezpiecznej tablicy.|  
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Niszczy deskryptor bezpiecznej tablicy.|  
|[COleSafeArray::Detach](#detach)|Odłącza **VARIANT** tablicy z `COleSafeArray` obiektu (tak, aby dane nie zostanie zwolniona).|  
|[COleSafeArray::GetByteArray](#getbytearray)|Kopiuje zawartość do bezpiecznej tablicy w [CByteArray](../../mfc/reference/cbytearray-class.md).|  
|[COleSafeArray::GetDim](#getdim)|Zwraca liczbę wymiarów tablicy.|  
|[COleSafeArray::GetElement](#getelement)|Pobiera jeden element bezpiecznej tablicy.|  
|[COleSafeArray::GetElemSize](#getelemsize)|Zwraca rozmiar w bajtach jeden element w bezpiecznej tablicy.|  
|[COleSafeArray::GetLBound](#getlbound)|Zwraca dolną granicę dla każdego wymiaru tablicy bezpiecznej.|  
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Zwraca liczbę elementów w jednowymiarowej tablicy `COleSafeArray` obiektu.|  
|[COleSafeArray::GetUBound](#getubound)|Zwraca górną granicę dla każdego wymiaru tablicy bezpiecznej.|  
|[COleSafeArray::Lock](#lock)|Zwiększa liczbę blokad tablicy i umieszczenie wskaźnika do tablicy danych w deskryptorze tablicy.|  
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Zwraca wskaźnik do elementu indeksowanego.|  
|[COleSafeArray::PutElement](#putelement)|Przypisuje pojedynczego elementu w tablicy.|  
|[COleSafeArray::Redim](#redim)|Zmienia najmniej znaczący granica (po prawej stronie) bezpiecznej tablicy.|  
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Liczba elementów w jednowymiarowa zmienia `COleSafeArray` obiektu.|  
|[COleSafeArray::UnaccessData](#unaccessdata)|Zmniejsza blokady liczba tablicy i unieważnia wskaźnika pobierane przez `AccessData`.|  
|[COleSafeArray::Unlock](#unlock)|Zmniejsza liczbę blokad tablicy, może być zwolniony lub zmiany rozmiaru.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Uzyskuje dostęp do odpowiadającego **VARIANT** struktury `COleSafeArray` obiektu.|  
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Uzyskuje dostęp do odpowiadającego **VARIANT** struktury `COleSafeArray` obiektu.|  
|[COleSafeArray::operator =](#operator_eq)|Kopiuje wartości do `COleSafeArray` obiektu ( **SAFEARRAY**, **VARIANT**, `COleVariant`, lub `COleSafeArray` tablicy).|  
|[COleSafeArray::operator ==](#operator_eq_eq)|Porównuje dwie tablice typu variant ( **SAFEARRAY**, **VARIANT**, `COleVariant`, lub `COleSafeArray` tablice).|  
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|Wyświetla zawartość `COleSafeArray` obiektu do kontekstu zrzutu.|  
  
## <a name="remarks"></a>Uwagi  
 `COleSafeArray` pochodną OLE **VARIANT** struktury. OLE **SAFEARRAY** funkcji elementów członkowskich są dostępne za pośrednictwem `COleSafeArray`, jak również jako zestaw funkcji Członkowskich zaprojektowane specjalnie dla jednowymiarowe tablice bajtów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="accessdata"></a>  COleSafeArray::AccessData  
 Pobiera wskaźnik do tablicy danych.  
  
```  
void AccessData(void** ppvData);
```  
  
### <a name="parameters"></a>Parametry  
 `ppvData`  
 Wskaźnik do wskaźnika do tablicy danych.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]  
  
##  <a name="allocdata"></a>  COleSafeArray::AllocData  
 Przydziela pamięć do bezpiecznej tablicy.  
  
```  
void AllocData();
```  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor  
 Przydziela pamięć dla deskryptora bezpiecznej tablicy.  
  
```  
void AllocDescriptor(DWORD dwDims);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDims`  
 Liczba wymiarów w bezpiecznej tablicy.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="attach"></a>  COleSafeArray::Attach  
 Zapewnia kontrolę nad danymi w istniejącym **VARIANT** tablicy do `COleSafeArray` obiektu.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *varSrc*  
 A **VARIANT** obiektu. *VarSrc* parametr musi mieć [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)**VT_ARRAY**.  
  
### <a name="remarks"></a>Uwagi  
 Źródło **VARIANT**jego typ jest ustawiony na `VT_EMPTY`. Ta funkcja usuwa bieżące dane tablicy ewentualne.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="clear"></a>  COleSafeArray::Clear  
 Czyści bezpiecznej tablicy.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja czyści bezpieczną tablicą przez ustawienie `VARTYPE` obiektu do `VT_EMPTY`. Bieżącą zawartość są wydawane i Tablica zostanie zwolniona.  
  
##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray  
 Konstruuje `COleSafeArray` obiektu.  
  
```  
COleSafeArray();

 
COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

 
COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);  
  
COleSafeArray(const COleSafeArray& saSrc);  
COleSafeArray(const VARIANT& varSrc);  
  COleSafeArray(LPCVARIANT pSrc);  
COleSafeArray(const COleVariant& varSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `saSrc`  
 Istniejące `COleSafeArray` obiektu lub **SAFEARRAY** ma zostać skopiowany do nowego `COleSafeArray` obiektu.  
  
 `vtSrc`  
 **VARTYPE** nowej `COleSafeArray` obiektu.  
  
 `psaSrc`  
 Wskaźnik do **SAFEARRAY** ma zostać skopiowany do nowego `COleSafeArray` obiektu.  
  
 *varSrc*  
 Istniejące **VARIANT** lub `COleVariant` obiekt ma zostać skopiowany do nowego `COleSafeArray` obiektu.  
  
 `pSrc`  
 Wskaźnik do **VARIANT** obiekt ma zostać skopiowany do nowego `COleSafeArray` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie te konstruktorów tworzenia nowych `COleSafeArray` obiektów. Jeśli istnieje żaden parametr pustą `COleSafeArray` obiekt jest tworzony ( `VT_EMPTY`). Jeśli `COleSafeArray` zostaną skopiowane z innego tablica której [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) znany jest niejawnie ( `COleSafeArray`, `COleVariant`, lub **VARIANT**), **VARTYPE** z Tablica źródłowa jest zachowywana i nie musi być określony. Jeśli `COleSafeArray` zostaną skopiowane z innego tablica której **VARTYPE** nie jest znany ( **SAFEARRAY**), **VARTYPE** musi zostać określona w `vtSrc` parametru.  
  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="copy"></a>  COleSafeArray::Copy  
 Tworzy kopię istniejącego bezpiecznej tablicy.  
  
```  
void Copy(LPSAFEARRAY* ppsa);
```  
  
### <a name="parameters"></a>Parametry  
 *ppsa*  
 Wskaźnik do lokalizacji, do której należy zwrócić nowego deskryptora tablicy.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="create"></a>  COleSafeArray::Create  
 Przydziela i inicjuje dane dla tablicy.  
  
```  
void Create(
    VARTYPE vtSrc,  
    DWORD dwDims,  
    DWORD* rgElements);

 
void Create(
    VARTYPE vtSrc,  
    DWORD dwDims,  
    SAFEARRAYBOUND* rgsabounds);
```  
  
### <a name="parameters"></a>Parametry  
 `vtSrc`  
 Typ podstawowy elementu tablicy (to znaczy **VARTYPE** każdego elementu w tablicy). **VARTYPE** jest ograniczony do podzbioru typów variant. Ani **VT_ARRAY** ani **VT_BYREF** flagę można ustawić. `VT_EMPTY` i **VT_NULL** nie są prawidłowe typy podstawowe dla tablicy. Wszystkie inne typy są prawnych.  
  
 `dwDims`  
 Liczba wymiarów tablicy. Można to zmienić po utworzeniu tablicy o [Redim](#redim).  
  
 *rgElements*  
 Wskaźnik do liczby elementów w tablicy dla każdego wymiaru tablicy.  
  
 *rgsabounds*  
 Wskaźnik do wektora granic (po jednej dla każdego wymiaru) do przydzielenia dla tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja spowoduje wyczyszczenie bieżące dane tablicy, w razie potrzeby. W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim  
 Tworzy nową jednowymiarowa `COleSafeArray` obiektu.  
  
```  
void CreateOneDim(
    VARTYPE vtSrc,  
    DWORD dwElements,  
    const void* pvSrcData = NULL,  
    long nLBound = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `vtSrc`  
 Typ podstawowy elementu tablicy (to znaczy **VARTYPE** każdego elementu w tablicy).  
  
 `dwElements`  
 Liczba elementów w tablicy. Można to zmienić po utworzeniu tablicy o [ResizeOneDim](#resizeonedim).  
  
 `pvSrcData`  
 Wskaźnik do danych można skopiować do tablicy.  
  
 *nLBound*  
 Dolna granica tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja przydziela i inicjuje dane dla tablicy kopiowanie określone dane, jeśli wskaźnik `pvSrcData` nie jest **NULL**.  
  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]  
  
##  <a name="destroy"></a>  COleSafeArray::Destroy  
 Niszczy istniejącego deskryptora tablicy i wszystkich danych w tablicy.  
  
```  
void Destroy();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekty są przechowywane w tablicy, każdy obiekt jest zwalniany. W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="destroydata"></a>  COleSafeArray::DestroyData  
 Niszczy wszystkich danych w bezpiecznej tablicy.  
  
```  
void DestroyData();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekty są przechowywane w tablicy, każdy obiekt jest zwalniany. W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor  
 Niszczy deskryptor bezpiecznej tablicy.  
  
```  
void DestroyDescriptor();
```  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="detach"></a>  COleSafeArray::Detach  
 Odłącza **VARIANT** danych z `COleSafeArray` obiektu.  
  
```  
VARIANT Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa **VARIANT** wartość w `COleSafeArray` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja odłącza dane w bezpiecznej tablicy przez ustawienie [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) obiektu do `VT_EMPTY`. Wywołującego odpowiedzialność za wolny tablicy przez wywołanie funkcji systemu Windows [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835).  
  
 W przypadku błędu, funkcja zwraca [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleSafeArray::PutElement](#putelement).  
  
##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray  
 Kopiuje zawartość do bezpiecznej tablicy w `CByteArray`.  
  
```  
void GetByteArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parametry  
 `bytes`  
 Odwołanie do [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu.  
  
##  <a name="getdim"></a>  COleSafeArray::GetDim  
 Zwraca liczbę wymiarów `COleSafeArray` obiektu.  
  
```  
DWORD GetDim();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wymiarów w bezpiecznej tablicy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="getelement"></a>  COleSafeArray::GetElement  
 Pobiera jeden element bezpiecznej tablicy.  
  
```  
void GetElement(
    long* rgIndices,  
    void* pvData);
```  
  
### <a name="parameters"></a>Parametry  
 `rgIndices`  
 Wskaźnik do tablicy indeksów dla każdego wymiaru tablicy.  
  
 `pvData`  
 Wskaźnik do elementu tablicy na położenie.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta automatycznie wywołuje funkcje systemu windows `SafeArrayLock` i `SafeArrayUnlock` przed i po pobraniu elementu. Jeśli element danych jest ciąg, obiekt lub typ variant, funkcja kopiuje element w prawidłowy sposób. Parametr `pvData` powinny wskazywać na dużej wystarczająco dużego buforu zawiera element.  
  
 W przypadku błędu, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]  
  
##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize  
 Pobiera rozmiar elementu w `COleSafeArray` obiektu.  
  
```  
DWORD GetElemSize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar w bajtach elementów bezpiecznej tablicy.  
  
##  <a name="getlbound"></a>  COleSafeArray::GetLBound  
 Zwraca dolną granicę do żadnego wymiaru `COleSafeArray` obiektu.  
  
```  
void GetLBound(
    DWORD dwDim,  
    long* pLBound);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDim`  
 Wymiar tablicy, do których chcesz pobrać dolnej granicy.  
  
 *pLBound*  
 Wskaźnik do lokalizacji zwraca dolną granicę.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, funkcja zwraca [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]  
  
##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize  
 Zwraca liczbę elementów w jednowymiarowej tablicy `COleSafeArray` obiektu.  
  
```  
DWORD GetOneDimSize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w bezpiecznym jednowymiarową.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="getubound"></a>  COleSafeArray::GetUBound  
 Zwraca górną granicę dla każdego wymiaru tablicy bezpiecznej.  
  
```  
void GetUBound(
    DWORD dwDim,  
    long* pUBound);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDim`  
 Wymiar tablicy, do których chcesz pobrać górną granicę.  
  
 *pUBound*  
 Wskaźnik do lokalizacji zwraca górną granicę.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, funkcja zwraca [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]  
  
##  <a name="lock"></a>  COleSafeArray::Lock  
 Zwiększa liczbę blokad tablicy i umieścić wskaźnik do tablicy danych w deskryptorze tablicy.  
  
```  
void Lock();
```  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu, zgłasza [COleException](../../mfc/reference/coleexception-class.md).  
  
 Wskaźnik w deskryptorze tablicy jest ważny do `Unlock` jest wywoływana. Wywołuje się `Lock` mogą być zagnieżdżane; równej liczby wywołań `Unlock` są wymagane.  
  
 Nie można usunąć tablicy, gdy jest on zablokowany.  
  
##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT  
 Wywołanie tego operatora rzutowania do dostępu do podstawowych **VARIANT** to struktura `COleSafeArray` obiektu.  
  
```  
operator LPCVARIANT() const;  
```  
  
##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT  
 Wywołanie tego operatora rzutowania do dostępu do podstawowych **VARIANT** to struktura `COleSafeArray` obiektu.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, zmienić wartość **VARIANT** struktury używane przez wskaźnik zwracane przez tę funkcję zmieni wartość tego `COleSafeArray` obiektu.  
  
##  <a name="operator_eq"></a>  COleSafeArray::operator =  
 Te operatory przypisania przeciążone skopiuj wartość źródła do tego `COleSafeArray` obiektu.  
  
```  
COleSafeArray& operator=(const COleSafeArray& saSrc);  
COleSafeArray& operator=(const VARIANT& varSrc);  
  COleSafeArray& operator=(LPCVARIANT pSrc);  
COleSafeArray& operator=(const COleVariant& varSrc);
```  
  
### <a name="remarks"></a>Uwagi  
 Krótki opis każdego operatora następująco:  
  
- **Operator = (** *saSrc* **)** umożliwia skopiowanie istniejącej `COleSafeArray` obiektu do tego obiektu.  
  
- **Operator = (** *varSrc ***)** umożliwia skopiowanie istniejącej **VARIANT** lub `COleVariant` tablicy do tego obiektu.  
  
- **Operator = (** `pSrc` **)** kopie **VARIANT** tablicy obiektów z niego `pSrc` do tego obiektu.  
  
##  <a name="operator_eq_eq"></a>  COleSafeArray::operator ==  
 Ten operator porównuje dwie tablice ( **SAFEARRAY**, **VARIANT**, `COleVariant`, lub `COleSafeArray` tablic) i zwraca wartość niezerową, jeśli są równe; w przeciwnym razie wartość 0.  
  
```  
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;  
   
BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;  
   
BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;  ```  
  
### Remarks  
 Two arrays are equal if they have an equal number of dimensions, equal size in each dimension, and equal element values.  
  
##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;  
 The `COleSafeArray` insertion (<<) operator supports diagnostic dumping and storing of a `COleSafeArray` object to an archive.  
  
```  
Operator CDumpContext & AFXAPI << (CDumpContext & kontrolera domeny,  
    COleSafeArray & saSrc);
```  
  
##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex  
 Returns a pointer to the element specified by the index values.  
  
```  
PtrOfIndex void (Liczba długa * rgIndices,  
    void ** ppvData);
```  
  
### Parameters  
 `rgIndices`  
 An array of index values that identify an element of the array. All indexes for the element must be specified.  
  
 `ppvData`  
 On return, pointer to the element identified by the values in `rgIndices`.  
  
##  <a name="putelement"></a>  COleSafeArray::PutElement  
 Assigns a single element into the array.  
  
```  
PutElement void (Liczba długa * rgIndices,  
    void * pvData);
```  
  
### Parameters  
 `rgIndices`  
 Pointer to an array of indexes for each dimension of the array.  
  
 `pvData`  
 Pointer to the data to assign to the array. **VT_DISPATCH**, **VT_UNKNOWN**, and `VT_BSTR` variant types are pointers and do not require another level of indirection.  
  
### Remarks  
 This function automatically calls the Windows functions [SafeArrayLock](https://msdn.microsoft.com/library/windows/desktop/ms221492.aspx) and [SafeArrayUnlock](https://msdn.microsoft.com/library/windows/desktop/ms221246.aspx) before and after assigning the element. If the data element is a string, object, or variant, the function copies it correctly, and if the existing element is a string, object, or variant, it is cleared correctly.  
  
 Note that you can have multiple locks on an array, so you can put elements into an array while the array is locked by other operations.  
  
 On error, the function throws a [CMemoryException](../../mfc/reference/cmemoryexception-class.md) or [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
 [!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]  
  
##  <a name="redim"></a>  COleSafeArray::Redim  
 Changes the least significant (rightmost) bound of a safe array.  
  
```  
Redim void (SAFEARRAYBOUND * psaboundNew);
```  
  
### Parameters  
 *psaboundNew*  
 Pointer to a new safe array bound structure containing the new array bound. Only the least significant dimension of an array may be changed.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim  
 Changes the number of elements in a one-dimensional `COleSafeArray` object.  
  
```  
void ResizeOneDim (DWORD dwElements);
```  
  
### Parameters  
 `dwElements`  
 Number of elements in the one-dimensional safe array.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData  
 Decrements the lock count of an array and invalidates the pointer retrieved by `AccessData`.  
  
```  
void UnaccessData();
```  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="unlock"></a>  COleSafeArray::Unlock  
 Decrements the lock count of an array so it can be freed or resized.  
  
```  
void Unlock();
```  
  
### Remarks  
 This function is called after access to the data in an array is finished. On error, it throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)
