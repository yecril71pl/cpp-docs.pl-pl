---
title: Klasa CComCurrency | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
dev_langs: C++
helpviewer_keywords: CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1e9466c2081b7d9622776702d367ccae64a36b4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcurrency-class"></a>Klasa CComCurrency
`CComCurrency`zawiera metody i operatory do tworzenia i zarządzania obiektem waluty.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComCurrency
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](#ccomcurrency)|Konstruktor `CComCurrency` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Zwraca adres `m_currency` element członkowski danych.|  
|[CComCurrency::GetFraction](#getfraction)|Wywołanie tej metody, aby zwrócić ułamkową część `CComCurrency` obiektu.|  
|[CComCurrency::GetInteger](#getinteger)|Wywołanie tej metody do zwrócenia całkowitą część `CComCurrency` obiektu.|  
|[CComCurrency::Round](#round)|Wywołanie tej metody do zaokrąglenia `CComCurrency` obiektu do najbliższej wartości całkowitej.|  
|[CComCurrency::SetFraction](#setfraction)|Wywołanie tej metody, aby ustawić ułamkową część `CComCurrency` obiektu.|  
|[CComCurrency::SetInteger](#setinteger)|Wywołanie tej metody można ustawić składnika całkowitą `CComCurrency` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCurrency::operator-](#operator_-)|Ten operator jest używana do wykonywania odejmowania na `CComCurrency` obiektu.|  
|[CComCurrency::operator! =](#operator_neq)|Porównuje dwa `CComCurrency` obiekty pod kątem nierówności.|  
|[CComCurrency::operator *](#operator_star)|Ten operator jest używana do wykonywania mnożenia na `CComCurrency` obiektu.|  
|[CComCurrency::operator * =](#operator_star_eq)|Ten operator jest używana do wykonywania mnożenia na `CComCurrency` obiektu i przypisz jej wynik.|  
|[CComCurrency::operator /](#operator_div)|Ten operator jest używana do wykonywania dzielenia na `CComCurrency` obiektu.|  
|[CComCurrency::operator / =](#operator_div_eq)|Ten operator jest używana do wykonywania dzielenia na `CComCurrency` obiektu i przypisz jej wynik.|  
|[CComCurrency::operator +](#operator_add)|Ten operator jest używany podczas dodawania `CComCurrency` obiektu.|  
|[CComCurrency::operator +=](#operator_add_eq)|Ten operator jest używany podczas dodawania `CComCurrency` obiektu i przypisz wynik do bieżącego obiektu.|  
|[CComCurrency::operator <](#operator_lt)|Ten operator porównuje dwa `CComCurrency` określają mniejszy obiekty.|  
|[CComCurrency::operator < =](#operator_lt_eq)|Ten operator porównuje dwa `CComCurrency` obiektów, aby ustalić równości lub mniejszy.|  
|[CComCurrency::operator =](#operator_eq)|Ten operator przypisuje `CComCurrency` obiektu na nową wartość.|  
|[CComCurrency::operator-=](#operator_-_eq)|Ten operator jest używana do wykonywania odejmowania na `CComCurrency` obiektu i przypisz jej wynik.|  
|[CComCurrency::operator ==](#operator_eq_eq)|Ten operator porównuje dwa `CComCurrency` obiekty pod kątem równości.|  
|[CComCurrency::operator >](#operator_gt)|Ten operator porównuje dwa `CComCurrency` obiektów, aby określić większy.|  
|[CComCurrency::operator > =](#operator_gt_eq)|Ten operator porównuje dwa `CComCurrency` obiektów, aby ustalić równości lub większy.|  
|[CComCurrency::operator waluty](#operator_currency)|Rzutowania `CURRENCY` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|`CURRENCY` Zmiennej utworzonej przez wystąpienie klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `CComCurrency`Otoka dla jest **waluty** — typ danych. **CURRENCY** jest zaimplementowany jako uzupełnienia do dwóch 8-bajtową wartość całkowitą skalowana przez 10 000. Dzięki temu stałoprzecinkową liczbę 15 cyfr z lewej strony punktu dziesiętnego i 4 cyfr z prawej strony. **Waluty** — typ danych jest niezwykle użyteczne obliczeń walutowych lub wszelkie obliczenia stałoprzecinkowe których dokładność jest ważna.  
  
 **CComCurrency** otoki implementuje operacje arytmetyczne, przypisywania i porównania dla tego typu stałoprzecinkowego. Obsługiwane aplikacje zostały wybrane do kontrolowania zaokrąglania błędów, które mogą wystąpić podczas stałoprzecinkowe obliczeń.  
  
 `CComCurrency` Obiektu zapewnia dostęp do cyfry po obu stronach przecinka w postaci dwóch składników: składnika liczba całkowita, służący do przechowywania wartości z lewej strony punktu dziesiętnego i ułamkowych składnik, który przechowuje wartość z prawej strony separatorem dziesiętnym. Ułamkowych części są przechowywane wewnętrznie jako wartość całkowitą z zakresu od-9999 ( **CY_MIN_FRACTION**) i +9999 ( **CY_MAX_FRACTION**). Metoda [CComCurrency::GetFraction](#getfraction) zwraca wartość skalowania o 10000 ( **CY_SCALE**).  
  
 Podczas określania liczby całkowitej i ułamkowych części **CComCurrency** obiektów, należy pamiętać, że składnik ułamkowych jest liczbą z przedziału od 0 do 9999. Jest to ważne podczas pracy nad waluty, takich jak dolara Amerykańskiego, który przedstawia kwoty przy użyciu tylko dwa cyfr znaczących po punkcie dziesiętnym. Mimo że nie są wyświetlane dwie ostatnie cyfry, musi być brana pod uwagę.  
  
|Wartość|Możliwe CComCurrency przypisania|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency(10,5000) *lub* CComCurrency(10.50)|  
|$10.05|CComCurrency(10,500) *lub* CComCurrency(10.05)|  
  
 Wartości **CY_MIN_FRACTION**, **CY_MAX_FRACTION**, i **CY_SCALE** są zdefiniowane w atlcur.h.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcur.h  
  
##  <a name="ccomcurrency"></a>CComCurrency::CComCurrency  
 Konstruktor.  
  
```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);  
CComCurrency(USHORT usSrc);  
CComCurrency(CHAR cSrc);  
CComCurrency(DOUBLE dSrc);  
CComCurrency(FLOAT fSrc);  
CComCurrency(LONG lSrc);  
CComCurrency(SHORT sSrc);  
CComCurrency(BYTE bSrc);  
CComCurrency(LONGLONG nInteger, SHORT nFraction);  
explicit CComCurrency(LPDISPATCH pDispSrc);  
explicit CComCurrency(const VARIANT& varSrc);  
explicit CComCurrency(LPCWSTR szSrc);  
explicit CComCurrency(LPCSTR szSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `curSrc`  
 Istniejące `CComCurrency` obiektu.  
  
 `cySrc`  
 Zmienna typu **waluty**.  
  
 `bSrc`, `dSrc`, `fSrc`, `lSrc`, *sSrc*, *ulSrc, usSrc*  
 Początkowa wartość zmiennej członkowskiej `m_currency`.  
  
 `cSrc`  
 Znak zawierający początkowej wartości do zmiennej członkowskiej `m_currency`.  
  
 `nInteger`, *nFraction*  
 Liczba całkowita i ułamkowych części wartość pieniężną. Zobacz [CComCurrency](../../atl/reference/ccomcurrency-class.md) Przegląd, aby uzyskać więcej informacji.  
  
 `pDispSrc`  
 `IDispatch` Wskaźnika.  
  
 *varSrc*  
 Zmienna typu **VARIANT**. Ustawienia regionalne bieżącego wątku służy do wykonywania konwersji.  
  
 `szSrc`  
 Ciąg Unicode lub ANSI zawierający wartości początkowej. Ustawienia regionalne bieżącego wątku służy do wykonywania konwersji.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor ustawia wartość początkową [CComCurrency::m_currency](#m_currency)i przyjmuje wiele różnych typów danych, w tym liczb całkowitych, ciągów, liczb zmiennoprzecinkowych **waluty** zmienne i inne `CComCurrency` obiektów. Jeśli wartość nie zostanie podana, `m_currency` jest równa 0.  
  
 W przypadku wystąpienia błędu, takie jak przepełnienia konstruktorów Brak specyfikacji wyjątku pusty ( **throw()**) wywołanie `AtlThrow` z opisem błędu HRESULT.  
  
 Korzystając z wartości zmiennoprzecinkowych lub podwójnym do przypisania wartości, należy pamiętać, że **CComCurrency(10.50)** jest odpowiednikiem **CComCurrency(10,5000)** i nie **CComCurrency(10,50)**.  
  
##  <a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr  
 Zwraca adres `m_currency` element członkowski danych.  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca adres `m_currency` element członkowski danych  
  
##  <a name="getfraction"></a>CComCurrency::GetFraction  
 Wywołanie tej metody, aby zwrócić ułamkową część `CComCurrency` obiektu.  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca część ułamkowa `m_currency` element członkowski danych.  
  
### <a name="remarks"></a>Uwagi  
 Ułamkowych części jest wartością całkowitą 4-cyfrowego między-9999 ( **CY_MIN_FRACTION**) i +9999 ( **CY_MAX_FRACTION**). `GetFraction`zwraca tę wartość skalowania przez 10000 ( **CY_SCALE**). Wartości **CY_MIN_FRACTION**, **CY_MAX_FRACTION**, i **CY_SCALE** są zdefiniowane w atlcur.h.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="getinteger"></a>CComCurrency::GetInteger  
 Wywołanie tej metody, aby uzyskać całkowitą część `CComCurrency` obiektu.  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca część całkowitą `m_currency` element członkowski danych.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="m_currency"></a>CComCurrency::m_currency  
 **Waluty** element członkowski danych.  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski przechowuje waluty dostępne i manipulowanie przez metody tej klasy.  
  
##  <a name="operator_-"></a>CComCurrency::operator-  
 Ten operator jest używana do wykonywania odejmowania na `CComCurrency` obiektu.  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CComCurrency` obiekt reprezentujący wynik odejmowania. W przypadku wystąpienia błędu, takie jak przepełnienia wywołuje tego operatora `AtlThrow` z opisem błędu HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="operator_neq"></a>CComCurrency::operator! =  
 Ten operator porównuje dwa obiekty pod kątem nierówności.  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli element porównywane nie jest równa `CComCurrency` obiektu; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="operator_star"></a>CComCurrency::operator *  
 Ten operator jest używana do wykonywania mnożenia na `CComCurrency` obiektu.  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Mnożnik.  
  
 `cur`  
 `CComCurrency` Używana jako mnożnik obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CComCurrency` obiekt reprezentujący wynik mnożenia. W przypadku wystąpienia błędu, takie jak przepełnienia wywołuje tego operatora `AtlThrow` z opisem błędu HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="operator_star_eq"></a>CComCurrency::operator * =  
 Ten operator jest używana do wykonywania mnożenia na `CComCurrency` obiektu i przypisz jej wynik.  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Mnożnik.  
  
 `cur`  
 `CComCurrency` Używana jako mnożnik obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienia wywołuje tego operatora `AtlThrow` z opisem błędu HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="operator_div"></a>CComCurrency::operator /  
 Ten operator jest używana do wykonywania dzielenia na `CComCurrency` obiektu.  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Dzielnik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CComCurrency` obiekt reprezentujący wyniku podziału. Jeżeli dzielnik wynosi 0, wystąpi błąd potwierdzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="operator_div_eq"></a>CComCurrency::operator / =  
 Ten operator jest używana do wykonywania dzielenia na `CComCurrency` obiektu i przypisz jej wynik.  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Dzielnik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CComCurrency` obiektu. Jeżeli dzielnik wynosi 0, wystąpi błąd potwierdzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="operator_add"></a>CComCurrency::operator +  
 Ten operator jest używany podczas dodawania `CComCurrency` obiektu.  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Obiekt ma zostać dodany do oryginalnego obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CComCurrency` obiekt reprezentujący wynik operacji dodawania. W przypadku wystąpienia błędu, takie jak przepełnienia wywołuje tego operatora `AtlThrow` z opisem błędu HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="operator_add_eq"></a>CComCurrency::operator +=  
 Ten operator jest używany podczas dodawania `CComCurrency` obiektu i przypisz wynik do bieżącego obiektu.  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienia wywołuje tego operatora `AtlThrow` z opisem błędu HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="operator_lt"></a>CComCurrency::operator&lt;  
 Ten operator porównuje dwa `CComCurrency` określają mniejszy obiekty.  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest mniejszy od drugiego, **false** inaczej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="operator_lt_eq"></a>CComCurrency::operator&lt;=  
 Ten operator porównuje dwa `CComCurrency` obiektów, aby ustalić równości lub mniejszy.  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest mniejszy niż drugi, **false** inaczej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="operator_eq"></a>CComCurrency::operator =  
 Ten operator przypisuje `CComCurrency` obiektu na nową wartość.  
  
```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `curSrc`  
 A **CComCurrency** obiektu.  
  
 `cySrc`  
 Zmienna typu **waluty**.  
  
 *sSrc*, `fSrc`, `lSrc`, *bSrc*, *usSrc*, `dSrc`, *cSrc*, *ulSrc*,`dSrc`  
 Liczbowa wartość do przypisania do `CComCurrency` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienia wywołuje tego operatora `AtlThrow` z opisem błędu HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="operator_-_eq"></a>CComCurrency::operator-=  
 Ten operator jest używana do wykonywania odejmowania na `CComCurrency` obiektu i przypisz jej wynik.  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CComCurrency` obiektu. W przypadku wystąpienia błędu, takie jak przepełnienia wywołuje tego operatora `AtlThrow` z opisem błędu HRESULT.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="operator_eq_eq"></a>CComCurrency::operator ==  
 Ten operator porównuje dwa `CComCurrency` obiekty pod kątem równości.  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Obiekt do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli obiekty są takie same (oznacza to, `m_currency` elementy członkowskie danych, zarówno integer wynikających z zaokrągleń zarówno obiekty mają taką samą wartość), **false** w przeciwnym razie wartość.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="operator_gt"></a>CComCurrency::operator&gt;  
 Ten operator porównuje dwa `CComCurrency` obiektów, aby określić większy.  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest większa od drugiej, **false** inaczej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="operator_gt_eq"></a>CComCurrency::operator&gt;=  
 Ten operator porównuje dwa `CComCurrency` obiektów, aby ustalić równości lub większy.  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli pierwszy obiekt jest większe lub równe drugiemu, **false** inaczej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="operator_currency"></a>CComCurrency::operator waluty  
 Operatory te służą do rzutowania `CComCurrency` do obiektu **waluty** — typ danych.  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do **waluty** obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="round"></a>CComCurrency::Round  
 Wywołanie tej metody do zaokrąglenia waluty do określonej liczby miejsc po przecinku.  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>Parametry  
 *nDecimals*  
 Liczba cyfr, do którego `m_currency` zostanie zaokrąglony w zakresie od 0 do 4.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="setfraction"></a>CComCurrency::SetFraction  
 Wywołanie tej metody, aby ustawić ułamkową część `CComCurrency` obiektu.  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>Parametry  
 *nFraction*  
 Wartość do przypisania do ułamkową część `m_currency` element członkowski danych. Znak ułamkowych części musi taka sama jak składnika całkowitą i wartość musi należeć do zakresu-9999 ( **CY_MIN_FRACTION**) do +9999 ( **CY_MAX_FRACTION**).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="setinteger"></a>CComCurrency::SetInteger  
 Wywołanie tej metody można ustawić składnika całkowitą `CComCurrency` obiektu.  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>Parametry  
 `nInteger`  
 Wartość do przypisania do składnika całkowitą `m_currency` element członkowski danych. Znak składnika liczba całkowita musi być zgodna znak istniejący składnik ułamkową.  
  
 `nInteger`musi zawierać się w zakresie **CY_MIN_INTEGER** do **CY_MAX_INTEGER** włącznie. Te wartości są definiowane w atlcur.h.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleCurrency](../../mfc/reference/colecurrency-class.md)   
 [WALUTY](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [Przegląd klas](../../atl/atl-class-overview.md)
