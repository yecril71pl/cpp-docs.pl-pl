---
title: Klasa CComGITPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90da5e8394ea4f630a817b68edf60d4242b40be9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884177"
---
# <a name="ccomgitptr-class"></a>Klasa CComGITPtr
Ta klasa dostarcza metody radzenia sobie z wskaźniki interfejsu i tabeli interfejsu globalnego (GIT).  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ wskaźnika interfejsu, które mają być przechowywane w usłudze GIT.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor.|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|Wywołaj tę metodę, aby zarejestrować wskaźnik interfejsu w tabeli interfejsu globalnego (GIT).|  
|[CComGITPtr::CopyTo](#copyto)|Wywołaj tę metodę, aby skopiować interfejs z tabeli interfejsu globalnego (GIT) do przekazanych wskaźnika.|  
|[CComGITPtr::Detach](#detach)|Wywołaj tę metodę, aby usunąć skojarzenie interfejsu z `CComGITPtr` obiektu.|  
|[CComGITPtr::GetCookie](#getcookie)|Wywołaj tę metodę, aby przywrócić plik cookie z `CComGITPtr` obiektu.|  
|[CComGITPtr::Revoke](#revoke)|Wywołaj tę metodę, aby usunąć interfejs z tabeli interfejsu globalnego (GIT).|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::operator typu DWORD.](#operator_dword)|Zwraca plik cookie z `CComGITPtr` obiektu.|  
|[CComGITPtr::operator =](#operator_eq)|Operator przypisania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Plik cookie.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekty, które agregacji marshaler trybu i muszą korzystać wskaźniki interfejsu uzyskane z innych obiektów, należy wykonać dodatkowe kroki, aby upewnić się, że interfejsy są organizowane poprawnie. Obejmuje to zwykle przechowywania wskaźniki interfejsu w GIT i uzyskiwanie wskaźnika z GIT każdorazowo, gdy jest używany. Klasa `CComGITPtr` znajduje się przydatne podczas używania wskaźniki interfejsu, przechowywane w usłudze GIT.  
  
> [!NOTE]
>  Możliwości tabeli interfejsu globalnego jest dostępna tylko na Windows 95, za pomocą modelu DCOM w wersji 1.1 i nowsze, Windows 98, Windows NT 4.0 z dodatkiem Service Pack 3 lub nowszym i Windows 2000.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="attach"></a>  CComGITPtr::Attach  
 Wywołaj tę metodę, aby zarejestrować wskaźnik interfejsu w tabeli interfejsu globalnego (GIT).  
  
```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Wskaźnik interfejsu, który ma zostać dodany do usługi GIT.  
  
 *dwCookie*  
 Plik cookie używany do identyfikowania wskaźnika interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania wystąpi błąd potwierdzenia, czy usługa GIT nie jest prawidłowy, czy plik cookie jest równa NULL.  
  
##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr  
 Konstruktor.  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *p*  
 Wskaźnik interfejsu do przechowywania w tabeli interfejsu globalnego (GIT).  
  
 [in] *git*  
 Odwołanie do istniejącego `CComGITPtr` obiektu.  
  
 [in] *dwCookie*  
 Plik cookie używany do identyfikowania wskaźnika interfejsu.  
  
 [in] *rv*  
 Źródło `CComGITPtr` przeniesienia danych z obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy nową `CComGITPtr` obiektu opcjonalnie przy użyciu istniejącego `CComGITPtr` obiektu.  
  
 Przy użyciu konstruktora *rv* jest konstruktora przenoszącego. Dane są przenoszone ze źródła, *rv*, a następnie *rv* jest wyczyszczone.  
  
##  <a name="dtor"></a>  CComGITPtr:: ~ CComGITPtr  
 Destruktor.  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa interfejs z tabeli interfejsu globalnego (GIT), za pomocą [CComGITPtr::Revoke](#revoke).  
  
##  <a name="copyto"></a>  CComGITPtr::CopyTo  
 Wywołaj tę metodę, aby skopiować interfejs z tabeli interfejsu globalnego (GIT) do przekazanych wskaźnika.  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *strony*  
 Wskaźnik, która będzie odbierać interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs z usługi GIT jest kopiowany do przekazanych wskaźnika. Wskaźnik muszą zostać zwolnione przez obiekt wywołujący, gdy nie jest już wymagany.  
  
##  <a name="detach"></a>  CComGITPtr::Detach  
 Wywołaj tę metodę, aby usunąć skojarzenie interfejsu z `CComGITPtr` obiektu.  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca plik cookie z `CComGITPtr` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 To obiekt wywołujący, aby usunąć interfejs z repozytorium GIT, za pomocą [CComGITPtr::Revoke](#revoke).  
  
##  <a name="getcookie"></a>  CComGITPtr::GetCookie  
 Wywołaj tę metodę, aby przywrócić plik cookie z `CComGITPtr` obiektu.  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pliku cookie.  
  
### <a name="remarks"></a>Uwagi  
 Plik cookie jest zmienną, używany do identyfikowania interfejsu i jego lokalizacji.  
  
##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie  
 Plik cookie.  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>Uwagi  
 Plik cookie jest zmienną członkowską, używany do identyfikowania interfejsu i jego lokalizacji.  
  
##  <a name="operator_eq"></a>  CComGITPtr::operator =  
 Operator przypisania.  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *p*  
 Wskaźnik do interfejsu.  
  
 [in] *git*  
 Odwołanie do `CComGITPtr` obiektu.  
  
 [in] *dwCookie*  
 Plik cookie używany do identyfikowania wskaźnika interfejsu.  
  
 [in] *rv*  
 `CComGITPtr` Do przenoszenia danych z.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowany `CComGITPtr` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Przypisuje nową wartość do `CComGITPtr` obiektu, albo z istniejącego obiektu lub odwołanie do tabeli interfejsu globalnego.  
  
##  <a name="operator_dword"></a>  CComGITPtr::operator typu DWORD.  
 Zwraca wartość pliku cookie skojarzona z `CComGITPtr` obiektu.  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Plik cookie jest zmienną, używany do identyfikowania interfejsu i jego lokalizacji.  
  
##  <a name="revoke"></a>  CComGITPtr::Revoke  
 Wywołaj tę metodę można usunąć bieżącego interfejsu z tabeli interfejsu globalnego (GIT).  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa interfejs z narzędzia GIT.  
  
## <a name="see-also"></a>Zobacz też  
 [Marshaler trybu](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Uzyskiwanie dostępu do interfejsów w Apartamentach](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [Kiedy używać tabeli interfejsu globalnego](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
