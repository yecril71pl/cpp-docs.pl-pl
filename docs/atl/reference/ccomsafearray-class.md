---
title: Klasa CComSafeArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
dev_langs: C++
helpviewer_keywords: CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5bfa67654bf86fdaadc9ef77c0d462b9796140d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomsafearray-class"></a>Klasa CComSafeArray
Ta klasa jest otoki dla **SAFEARRAY** struktury.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych, które mają być przechowywane w tablicy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSafeArray::CComSafeArray](#ccomsafearray)|Konstruktor.|  
|[CComSafeArray:: ~ CComSafeArray](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSafeArray::Add](#add)|Dodaje jeden lub więcej elementów, lub **SAFEARRAY** struktury do `CComSafeArray`.|  
|[CComSafeArray::Attach](#attach)|Dołącza **SAFEARRAY** struktury do `CComSafeArray` obiektu.|  
|[CComSafeArray::CopyFrom](#copyfrom)|Kopiuje zawartość **SAFEARRAY** struktury w `CComSafeArray` obiektu.|  
|[CComSafeArray::CopyTo](#copyto)|Tworzy kopię `CComSafeArray` obiektu.|  
|[CComSafeArray::Create](#create)|Tworzy `CComSafeArray` obiektu.|  
|[CComSafeArray::Destroy](#destroy)|Niszczy `CComSafeArray` obiektu.|  
|[CComSafeArray::Detach](#detach)|Odłącza **SAFEARRAY** z `CComSafeArray` obiektu.|  
|[CComSafeArray::GetAt](#getat)|Pobiera pojedynczego elementu z tablicy jednowymiarowej.|  
|[CComSafeArray::GetCount](#getcount)|Zwraca liczbę elementów w tablicy.|  
|[CComSafeArray::GetDimensions](#getdimensions)|Zwraca liczbę wymiarów tablicy.|  
|[CComSafeArray::GetLowerBound](#getlowerbound)|Zwraca dolną granicę określonego wymiaru tablicy.|  
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Zwraca adres `m_psa` element członkowski danych.|  
|[CComSafeArray::GetType](#gettype)|Zwraca typ danych przechowywanych w tablicy.|  
|[CComSafeArray::GetUpperBound](#getupperbound)|Zwraca górną granicę dla każdego wymiaru tablicy.|  
|[CComSafeArray::IsSizable](#issizable)|Sprawdza, czy `CComSafeArray` obiektu można zmieniać.|  
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Pobiera pojedynczego elementu z tablicy wielowymiarowej.|  
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Ustawia wartość elementu w tablicy wielowymiarowej.|  
|[CComSafeArray::Resize](#resize)|Zmienia rozmiar `CComSafeArray` obiektu.|  
|[CComSafeArray::SetAt](#setat)|Ustawia wartość elementu w tablicy jednowymiarowej.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Rzutuje wartość **SAFEARRAY** wskaźnika.|  
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Pobiera element z tablicy.|  
|[CComSafeArray::operator =](#operator_eq)|Operator przypisania.|  

  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSafeArray::m_psa](#m_psa)|Ten element członkowski danych przechowuje adres **SAFEARRAY** struktury.|  
  
## <a name="remarks"></a>Uwagi  
 `CComSafeArray`udostępnia otokę dla [— typ danych parametru SAFEARRAY](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e) klasy, dzięki czemu polegać na tworzenie i zarządzanie nimi jedno - i są one Wielowymiarowe tablice z niemal dowolnego typu VARIANT, obsługiwane.  
  
 `CComSafeArray`Przekazywanie tablic między procesami upraszcza, a ponadto zapewnia dodatkowe zabezpieczenia sprawdzając wartości indeksu tablicy względem górnej i dolne granice tablicy.  
  
 Dolna granica `CComSafeArray` można uruchomić w dowolnej wartości zdefiniowanej przez użytkownika; jednak używać tablic, które są dostępne za pośrednictwem C++ dolna granica 0. Innych języków, takich jak Visual Basic może użyć innych wartości obwiedni (na przykład -10-10).  
  
 Użyj [CComSafeArray::Create](#create) utworzyć `CComSafeArray` obiektu, a [CComSafeArray::Destroy](#destroy) go usunąć.  
  
 A `CComSafeArray` może zawierać następujące podzbiór typów danych VARIANT:  
  
|VARTYPE|Opis|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ULONGLONG|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|decimal wskaźnika|  
|VT_VARIANT|wskaźnik typu Variant|  
|VT_CY|Currency — Typ danych|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsafe.h  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]  
  
##  <a name="add"></a>CComSafeArray::Add  
 Dodaje jeden lub więcej elementów, lub **SAFEARRAY** struktury do `CComSafeArray`.  
  
```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `psaSrc`  
 Wskaźnik do **SAFEARRAY** obiektu.  
  
 `ulCount`  
 Liczba obiektów, aby dodać do tablicy.  
  
 *pT*  
 Wskaźnik do co najmniej jeden obiekt ma zostać dodany do tablicy.  
  
 *t*  
 Odwołanie do obiektu, który ma zostać dodany do tablicy.  
  
 `bCopy`  
 Wskazuje, czy należy utworzyć kopię danych. Wartość domyślna to **TRUE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Nowe obiekty są dodawane na końcu istniejącej **SAFEARRAY** obiektu. Dodawanie obiektu do wielowymiarowe **SAFEARRAY** obiekt nie jest obsługiwany. Podczas dodawania istniejącej tablicy obiektów, zarówno tablic musi zawierać elementów tego samego typu.  
  
 `bCopy` Flaga jest brana pod uwagę podczas elementów typu `BSTR` lub **VARIANT** są dodawane do tablicy. Wartość domyślna **TRUE** zapewnia, że nowa kopia jest wykonany danych, gdy element zostanie dodany do tablicy.  
  
##  <a name="attach"></a>CComSafeArray::Attach  
 Dołącza **SAFEARRAY** struktury do `CComSafeArray` obiektu.  
  
```
HRESULT Attach(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `psaSrc`  
 Wskaźnik do **SAFEARRAY** struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Dołącza **SAFEARRAY** struktury do `CComSafeArray` obiektu, co istniejący `CComSafeArray` dostępnych metod.  
  
##  <a name="ccomsafearray"></a>CComSafeArray::CComSafeArray  
 Konstruktor.  
  
```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `bound`  
 A **SAFEARRAYBOUND** struktury.  
  
 `ulCount`  
 Liczba elementów w tablicy.  
  
 `lLBound`  
 Dolna granica wartości; oznacza to, że indeks pierwszego elementu w tablicy.  
  
 `pBound`  
 Wskaźnik do **SAFEARRAYBOUND** struktury.  
  
 `uDims`  
 Liczba wymiarów tablicy.  
  
 `saSrc`  
 Odwołanie do **SAFEARRAY** struktury lub `CComSafeArray` obiektu. W obu przypadkach konstruktora używa tego odwołania do skopiowania tablicy, więc tablicy nie jest wywoływany po wykonaniu konstrukcji.  
  
 `psaSrc`  
 Wskaźnik do **SAFEARRAY** struktury. Konstruktor używa tego adresu do skopiowania tablicy, więc tablicy nie jest wywoływany po wykonaniu konstrukcji.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy `CComSafeArray` obiektu.  
  
##  <a name="dtor"></a>CComSafeArray:: ~ CComSafeArray  
 Destruktor.  
  
```
~CComSafeArray() throw()
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="copyfrom"></a>CComSafeArray::CopyFrom  
 Kopiuje zawartość **SAFEARRAY** struktury w `CComSafeArray` obiektu.  
  
```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parametry  
 `ppArray`  
 Wskaźnik do **SAFEARRAY** do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia skopiowanie zawartości **SAFEARRAY** do bieżącego `CComSafeArray` obiektu. Zastępuje istniejącą zawartość elementu tablicy.  
  
##  <a name="copyto"></a>CComSafeArray::CopyTo  
 Tworzy kopię `CComSafeArray` obiektu.  
  
```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parametry  
 `ppArray`  
 Wskaźnik do lokalizacji, w której chcesz utworzyć nowe **SAFEARRAY**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia skopiowanie zawartości `CComSafeArray` obiekt do **SAFEARRAY** struktury.  
  
##  <a name="create"></a>CComSafeArray::Create  
 Tworzy `CComSafeArray`.  
  
```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pBound`  
 Wskaźnik do **SAFEARRAYBOUND** obiektu.  
  
 `uDims`  
 Liczba wymiarów tablicy.  
  
 `ulCount`  
 Liczba elementów w tablicy.  
  
 `lLBound`  
 Dolna granica wartości; oznacza to, że indeks pierwszego elementu w tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 A `CComSafeArray` można utworzyć obiektu z istniejącego **SAFEARRAYBOUND** struktury i liczba wymiarów lub określając liczbę elementów w tablicy oraz dolną granicę. Jeśli tablica jest udostępniany z języka Visual C++, dolna granica musi mieć wartość 0. Inne języki mogą zezwalać innych wartości dolna granica (na przykład Visual Basic obsługuje tablice elementów z zakresem, takich jak -10-10).  
  
##  <a name="destroy"></a>CComSafeArray::Destroy  
 Niszczy `CComSafeArray` obiektu.  
  
```
HRESULT Destroy();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Niszczy istniejącą `CComSafeArray` obiekt i wszystkie dane w nim zawarte.  
  
##  <a name="detach"></a>CComSafeArray::Detach  
 Odłącza **SAFEARRAY** z `CComSafeArray` obiektu.  
  
```
LPSAFEARRAY Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do **SAFEARRAY** obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda odłącza **SAFEARRAY** obiekt z `CComSafeArray` obiektu.  
  
##  <a name="getat"></a>CComSafeArray::GetAt  
 Pobiera pojedynczego elementu z tablicy jednowymiarowej.  
  
```
T& GetAt(LONG lIndex) const;
```  
  
### <a name="parameters"></a>Parametry  
 `lIndex`  
 Numer indeksu wartości w tablicy do zwrócenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do elementu tablicy wymagane.  
  
##  <a name="getcount"></a>CComSafeArray::GetCount  
 Zwraca liczbę elementów w tablicy.  
  
```
ULONG GetCount(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `uDim`  
 Wymiar tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku użycia z tablicy wielowymiarowej, ta metoda zwróci liczbę elementów tylko określonego wymiaru.  
  
##  <a name="getdimensions"></a>CComSafeArray::GetDimensions  
 Zwraca liczbę wymiarów tablicy.  
  
```
UINT GetDimensions() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę wymiarów tablicy.  
  
##  <a name="getlowerbound"></a>CComSafeArray::GetLowerBound  
 Zwraca dolną granicę określonego wymiaru tablicy.  
  
```
LONG GetLowerBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `uDim`  
 Wymiar tablicy, do których chcesz pobrać dolnej granicy. W przypadku pominięcia będzie używana wartość domyślna to 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dolną granicę.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli dolna granica jest równa 0, oznacza to tablicy notacji języka C, w których pierwszy element to element o numerze 0. W przypadku wystąpienia błędu, na przykład wymiar nieprawidłowy argument, ta metoda wywołuje `AtlThrow` z opisem błędu HRESULT.  
  
##  <a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr  
 Zwraca adres `m_psa` element członkowski danych.  
  
```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do [CComSafeArray::m_psa](#m_psa) element członkowski danych.  
  
##  <a name="gettype"></a>CComSafeArray::GetType  
 Zwraca typ danych przechowywanych w tablicy.  
  
```
VARTYPE GetType() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca typ danych przechowywanych w tablicy, która może być jedną z następujących typów:  
  
|VARTYPE|Opis|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ULONGLONG|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|decimal wskaźnika|  
|VT_VARIANT|wskaźnik typu Variant|  
|VT_CY|Currency — Typ danych|  
  
##  <a name="getupperbound"></a>CComSafeArray::GetUpperBound  
 Zwraca górną granicę dla każdego wymiaru tablicy.  
  
```
LONG GetUpperBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `uDim`  
 Wymiar tablicy, do których chcesz pobrać górną granicę. W przypadku pominięcia będzie używana wartość domyślna to 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca górną granicę. Ta wartość jest włącznie, maksymalna wartość indeksu prawidłowy dla tego wymiaru.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku wystąpienia błędu, na przykład wymiar nieprawidłowy argument, ta metoda wywołuje `AtlThrow` z opisem błędu HRESULT.  
  
##  <a name="issizable"></a>CComSafeArray::IsSizable  
 Sprawdza, czy `CComSafeArray` obiektu można zmieniać.  
  
```
bool IsSizable() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli `CComSafeArray` można zmieniać, **false** Jeśli nie jest możliwy.  
  
##  <a name="m_psa"></a>CComSafeArray::m_psa  
 Zawiera adres **SAFEARRAY** uzyskać dostępu do struktury.  
  
```
LPSAFEARRAY m_psa;
```  
  
##  <a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt  
 Pobiera pojedynczego elementu z tablicy wielowymiarowej.  
  
```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```  
  
### <a name="parameters"></a>Parametry  
 `alIndex`  
 Wskaźnik do wektor indeksów dla każdego wymiaru tablicy. Wymiar (najbardziej znaczących) po lewej stronie jest `alIndex[0]`.  
  
 *t*  
 Zwracane jest odwołanie do danych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt  
 Ustawia wartość elementu w tablicy wielowymiarowej.  
  
```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 `alIndex`  
 Wskaźnik do wektor indeksów dla każdego wymiaru tablicy. Wymiar (najmniej znaczący) po prawej stronie jest `alIndex`[0].  
  
 *T*  
 Określa wartość nowego elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 To jest wersja wielowymiarowe [CComSafeArray::SetAt](#setat).  
  
##  <a name="operator_at"></a>CComSafeArray::operator\[\]  
 Pobiera element z tablicy.  
  
```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```  
  
### <a name="parameters"></a>Parametry  
 *wartość, nIndex lindex.*  
 Numer indeksu wymaganego elementu w tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element odpowiednie tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Pełni podobną funkcję do [CComSafeArray::GetAt](#getat), jednak ten operator działa tylko tablice jednowymiarowe.  
  
##  <a name="operator_eq"></a>CComSafeArray::operator =  
 Operator przypisania.  
  
```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `saSrc`  
 Odwołanie do `CComSafeArray` obiektu.  
  
 `psaSrc`  
 Wskaźnik do **SAFEARRAY** obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca typ danych przechowywanych w tablicy.  
  
##  <a name="operator_lpsafearray"></a>CComSafeArray::operator LPSAFEARRAY  
 Rzutuje wartość **SAFEARRAY** wskaźnika.  
  
```
operator LPSAFEARRAY() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rzutuje wartość **SAFEARRAY** wskaźnika.  
  
##  <a name="resize"></a>CComSafeArray::Resize  
 Zmienia rozmiar `CComSafeArray` obiektu.  
  
```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pBound`  
 Wskaźnik do **SAFEARRAYBOUND** strukturę, która zawiera informacje na temat liczby elementów i dolną granicę tablicy.  
  
 `ulCount`  
 Żądana liczba obiektów w tablicy, którego rozmiar jest zmieniany.  
  
 `lLBound`  
 Dolna granica.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zmienia rozmiar tylko ostatni wymiar. Nie zmieni się rozmiar tablic zwracających **IsResizable** jako **false**.  
  
##  <a name="setat"></a>CComSafeArray::SetAt  
 Ustawia wartość elementu w tablicy jednowymiarowej.  
  
```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lIndex`  
 Numer indeksu można ustawić elementu tablicy.  
  
 *t*  
 Nowa wartość określonego elementu.  
  
 `bCopy`  
 Wskazuje, czy należy utworzyć kopię danych. Wartość domyślna to **TRUE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 `bCopy` Flaga jest brana pod uwagę podczas elementów typu `BSTR` lub **VARIANT** są dodawane do tablicy. Wartość domyślna **TRUE** zapewnia, że nowa kopia jest wykonany danych, gdy element zostanie dodany do tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 [Typ danych parametru SAFEARRAY](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray::Create](#create)   
 [CComSafeArray::Destroy](#destroy)   
 [Przegląd klas](../../atl/atl-class-overview.md)
