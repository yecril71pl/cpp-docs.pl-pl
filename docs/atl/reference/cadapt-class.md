---
title: Klasa CAdapt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
dev_langs:
- C++
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cabdf0a396f50f548cbe01a765411120ff7dd9f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cadapt-class"></a>Klasa CAdapt
Ten szablon jest używany do opakowywania klas, które ponownie definiują operator address-of, aby zwrócić coś innego niż adres obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class CAdapt
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dostosowany.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAdapt::CAdapt](#cadapt)|Konstruktor.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAdapt::operator const T &](#operator_const_t_amp)|Zwraca `const` odwołanie do `m_T`.|  
|[CAdapt::operator T &](#operator_t_amp)|Zwraca odwołanie do `m_T`.|  
|[CAdapt::operator <](#operator_lt)|Porównuje obiekt typu dostosowane z `m_T`.|  
|[CAdapt::operator =](#operator_eq)|Przypisuje obiektu typu dostosowane do `m_T`.|  
|[CAdapt::operator ==](#operator_eq_eq)|Porównuje obiekt typu dostosowane z `m_T`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAdapt::m_T](#m_t)|Dostosowywane dane.|  
  
## <a name="remarks"></a>Uwagi  
 `CAdapt` jest to prosty szablon stosowanego do opakowywania klasy, które ponownie zdefiniować operator address-of ( `operator &`) do zwrócenia coś innego niż adres obiektu. Tego rodzaju przykładów w ATL `CComBSTR`, `CComPtr`, i `CComQIPtr` klasy i klasę obsługa kompilatora COM `_com_ptr_t`. Te klasy wszystkich ponownie zdefiniować operator address-of, aby zwrócić adres ich elementy członkowskie danych ( `BSTR` w odniesieniu `CComBSTR`i wskaźnika interfejsu w przypadku innych klas).  
  
 `CAdapt`w jest ukrycie operator address-of zdefiniowane przez klasę podstawową rolą `T`, jeszcze nadal zachowują właściwości klasy dostosowane. `CAdapt` spełnia tej roli, przytrzymując publicznego elementu członkowskiego [m_T](#m_t), typu `T`i definiując operatory konwersji, operatory porównania i konstruktora kopiującego, aby umożliwić specjalizacjach `CAdapt` traktowane jak obiekty typu `T`.  
  
 Klasa karty `CAdapt` jest przydatne, ponieważ niektóre klasy kontenera stylu oczekują możliwości uzyskuje adresy ich zawarte obiekty przy użyciu operatora adresu. Ponowne zdefiniowanie operatora address-of może spowodować problemy z tym wymaganiem, zazwyczaj powoduje błędy kompilacji i uniemożliwia wykorzystywanie typu niezaadaptowanego z klasami, które oczekują, że „po prostu ma działać”. `CAdapt` Umożliwia wokół tych problemów.  
  
 Zazwyczaj będzie używać `CAdapt` Jeśli chcesz przechowywać `CComBSTR`, `CComPtr`, `CComQIPtr`, lub `_com_ptr_t` obiektów w klasie stylu kontenera. To najczęściej niezbędne do obsługi standardu C ++ 11 przed kontenery standardowa biblioteka C++, ale kontenery 11 standardowa biblioteka języka C ++ automatycznie pracować z typów, które mają przeciążony `operator&()`. Standardowa biblioteka osiąga to przy użyciu wewnętrznie [std::addressof](../../standard-library/memory-functions.md#addressof) można uzyskać wartość true, adresy obiektów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  
  
##  <a name="cadapt"></a>  CAdapt::CAdapt  
 Konstruktory zezwala na być domyślnie wykonane, skopiowanych z obiektu typu dostosowane lub skopiowanych z innego obiektu karty obiektu karty.  
  
```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Zmienna typu dostosowuje się do skopiowania do obiektu nowo utworzone karty.  
  
 *rSrCA*  
 Obiekt karta którego zawartych w niej dane powinny zostać skopiowane (lub przeniesione) w obiekcie nowo utworzone karty.  
  
##  <a name="m_t"></a>  CAdapt::m_T  
 Przechowuje dane są dostosowywane.  
  
```
T m_T;
```  
  
### <a name="remarks"></a>Uwagi  
 To **publicznego** elementu członkowskiego danych jest możliwy bezpośrednio lub pośrednio z [operator const T &](#operator_const_t_amp) i [operator T &](#operator_t_amp).  
  
##  <a name="operator_const_t_amp"></a>  CAdapt::operator const T&amp;  
 Zwraca **const** odwołanie do [m_T](#m_t) — członek, umożliwiając obiekt Karta traktowane jakby był typu obiektu `T`.  
  
```  
operator const T&() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **const** odwołanie do `m_T`.  
  
##  <a name="operator_t_amp"></a>  CAdapt::operator T&amp;  
 Zwraca odwołanie do [m_T](#m_t) — członek, umożliwiając obiekt Karta traktowane jakby był typu obiektu `T`.  
  
```  
operator T&();
```     
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `m_T`.  
  
##  <a name="operator_lt"></a>  CAdapt::operator &lt;  
 Porównuje obiekt typu dostosowane z [m_T](#m_t).  
  
```
bool operator<(const T& rSrc) const;
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odwołanie do obiektu, który ma zostać porównane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik porównania `m_T` i `rSrc`.  
  
##  <a name="operator_eq"></a>  CAdapt::operator =  
 Operator przypisania przypisuje argumentu, `rSrc`, do elementu członkowskiego danych [m_T](#m_t) i zwraca bieżącego obiektu karty.  
  
```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odwołanie do obiektu typu dostosowane do skopiowania. 

 `rSrCA` Odwołanie do obiektu do przeniesienia. 
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego obiektu.  
  
##  <a name="operator_eq_eq"></a>  CAdapt::operator ==  
 Porównuje obiekt typu dostosowane z [m_T](#m_t).  
  
```
bool operator== (const T& rSrc) const;
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odwołanie do obiektu, który ma zostać porównane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik porównania `m_T` i `rSrc`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
