---
title: Klasa CComGITPtr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c001d0d1ca8e756b24d97051d100e7d71723569c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomgitptr-class"></a>Klasa CComGITPtr
Ta klasa dostarcza metody zajmujących się wskaźniki interfejsu i tabela interfejsu globalnego (GIT).  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ wskaźnika interfejsu, aby były przechowywane w usłudze GIT.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor.|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|Wywołaj tę metodę, aby zarejestrować wskaźnika interfejsu w Tabela interfejsu globalnego (GIT).|  
|[CComGITPtr::CopyTo](#copyto)|Wywołaj tę metodę w celu skopiowania interfejsu Tabela interfejsu globalnego (GIT) na wskaźnik przekazany.|  
|[CComGITPtr::Detach](#detach)|Wywołanie tej metody, aby usunąć skojarzenie interfejsu z `CComGITPtr` obiektu.|  
|[CComGITPtr::GetCookie](#getcookie)|Wywołanie tej metody, aby przywrócić plik cookie z `CComGITPtr` obiektu.|  
|[CComGITPtr::Revoke](#revoke)|Wywołaj tę metodę, aby usunąć interfejs z Tabela interfejsu globalnego (GIT).|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|Zwraca plik cookie z `CComGITPtr` obiektu.|  
|[CComGITPtr::operator =](#operator_eq)|Operator przypisania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Plik cookie.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekty agregacji Organizator trybu wolnych wątków, które muszą używać wskaźniki interfejsu uzyskane z innych obiektów muszą wykonać dodatkowe czynności, aby upewnić się, że interfejsy są poprawnie przekazywane. Obejmuje to zwykle przechowywania wskaźniki interfejsu w usłudze GIT i uzyskiwanie wskaźnika z GIT każdym razem, gdy jest używany. Klasa `CComGITPtr` podano ułatwiają wskaźniki interfejsu przechowywane w usłudze GIT.  
  
> [!NOTE]
>  Funkcji Tabela interfejsu globalnego jest dostępna tylko na system Windows 95 z modelu DCOM w wersji 1.1 i nowsze, Windows 98, Windows NT 4.0 z dodatkiem Service Pack 3 lub nowszym i Windows 2000.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="attach"></a>CComGITPtr::Attach  
 Wywołaj tę metodę, aby zarejestrować wskaźnika interfejsu w Tabela interfejsu globalnego (GIT).  
  
```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik interfejsu, który ma zostać dodany do GIT.  
  
 `dwCookie`  
 Plik cookie używany do identyfikowania wskaźnika interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania wystąpi błąd potwierdzenia, czy usługa GIT nie jest prawidłowy, czy plik cookie jest równa NULL.  
  
##  <a name="ccomgitptr"></a>CComGITPtr::CComGITPtr  
 Konstruktor.  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`p`  
 Wskaźnik interfejsu mają być przechowywane w tabeli interfejsu globalnego (GIT).  
  
 [in]`git`  
 Odwołanie do istniejącej `CComGITPtr` obiektu.  
  
 [in]`dwCookie`  
 Plik cookie używany do identyfikowania wskaźnika interfejsu.  
  
 [in]`rv`  
 Źródło `CComGITPtr` obiektu do przeniesienia danych z.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy nowy `CComGITPtr` obiektu, opcjonalnie przy użyciu istniejącego `CComGITPtr` obiektu.  
  
 Przy użyciu konstruktora `rv` jest konstruktor przenoszenia. Dane jest przenoszony ze źródła, `rv`, a następnie `rv` jest wyczyszczone.  
  
##  <a name="dtor"></a>CComGITPtr:: ~ CComGITPtr  
 Destruktor.  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa interfejs z Tabela interfejsu globalnego (GIT), za pomocą [CComGITPtr::Revoke](#revoke).  
  
##  <a name="copyto"></a>CComGITPtr::CopyTo  
 Wywołaj tę metodę w celu skopiowania interfejsu Tabela interfejsu globalnego (GIT) na wskaźnik przekazany.  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 Wskaźnik, która będzie odbierać interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs z repozytorium GIT jest kopiowana na wskaźnik przekazany. Wskaźnik muszą zostać zwolnione przez obiekt wywołujący, gdy nie jest już wymagane.  
  
##  <a name="detach"></a>CComGITPtr::Detach  
 Wywołanie tej metody, aby usunąć skojarzenie interfejsu z `CComGITPtr` obiektu.  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca plik cookie z `CComGITPtr` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jest obiekt wywołujący, aby usunąć interfejs z repozytorium GIT, za pomocą [CComGITPtr::Revoke](#revoke).  
  
##  <a name="getcookie"></a>CComGITPtr::GetCookie  
 Wywołanie tej metody, aby przywrócić plik cookie z `CComGITPtr` obiektu.  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca plik cookie.  
  
### <a name="remarks"></a>Uwagi  
 Plik cookie jest zmienną używane do identyfikowania interfejs i jego lokalizacji.  
  
##  <a name="m_dwcookie"></a>CComGITPtr::m_dwCookie  
 Plik cookie.  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>Uwagi  
 Plik cookie jest zmienną członkowską używane do identyfikowania interfejs i jego lokalizacji.  
  
##  <a name="operator_eq"></a>CComGITPtr::operator =  
 Operator przypisania.  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`p`  
 Wskaźnik do interfejsu.  
  
 [in]`git`  
 Odwołanie do `CComGITPtr` obiektu.  
  
 [in]`dwCookie`  
 Plik cookie używany do identyfikowania wskaźnika interfejsu.  
  
 [in]`rv`  
 `CComGITPtr` Do przeniesienia danych z.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CComGITPtr` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Przypisuje nową wartość do `CComGITPtr` obiektu, albo z istniejącego obiektu lub odwołanie do tabeli interfejsu globalnego.  
  
##  <a name="operator_dword"></a>CComGITPtr::operator DWORD  
 Zwraca plik cookie skojarzone z `CComGITPtr` obiektu.  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Plik cookie jest zmienną używane do identyfikowania interfejs i jego lokalizacji.  
  
##  <a name="revoke"></a>CComGITPtr::Revoke  
 Wywołaj tę metodę, aby usunąć bieżący interfejs z Tabela interfejsu globalnego (GIT).  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa interfejs z repozytorium GIT.  
  
## <a name="see-also"></a>Zobacz też  
 [Organizator trybu wolnych wątków](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Uzyskiwanie dostępu do interfejsów w Apartamentach](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [Kiedy należy używać Tabela interfejsu globalnego](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Przegląd klas](../../atl/atl-class-overview.md)
