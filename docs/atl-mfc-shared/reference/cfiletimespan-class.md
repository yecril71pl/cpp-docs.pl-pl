---
title: Klasa CFileTimeSpan
ms.date: 10/18/2018
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: f9bb42ba4c142f671a83dcfa7e99cff940fff047
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491294"
---
# <a name="cfiletimespan-class"></a>Klasa CFileTimeSpan

Ta klasa zapewnia metody zarządzania względnymi wartościami daty i godziny skojarzonych z plikiem.

## <a name="syntax"></a>Składnia

```
class CFileTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Wywołaj tę metodę, aby pobrać przedział czasu `CFileTimeSpan` z obiektu.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Wywołaj tę metodę, aby ustawić przedział `CFileTimeSpan` czasu obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan:: operator-](#operator_-)|Wykonuje odejmowanie `CFileTimeSpan` obiektu.|
|[CFileTimeSpan:: operator! =](#operator_neq)|Porównuje `CFileTimeSpan` dwa obiekty pod kątem nierówności.|
|[CFileTimeSpan:: operator +](#operator_add)|Wykonuje Dodawanie do `CFileTimeSpan` obiektu.|
|[CFileTimeSpan:: operator + =](#operator_add_eq)|Wykonuje Dodawanie `CFileTimeSpan` do obiektu i przypisuje wynik do bieżącego obiektu.|
|[CFileTimeSpan:: operator&lt;](#operator_lt)|Porównuje `CFileTimeSpan` dwa obiekty, aby określić, że są one mniejsze.|
|[CFileTimeSpan:: operator&lt;=](#operator_lt_eq)|Porównuje `CFileTimeSpan` dwa obiekty, aby określić równość lub mniejszą.|
|[CFileTimeSpan:: operator =](#operator_eq)|Operator przypisania.|
|[CFileTimeSpan:: operator-=](#operator_-_eq)|Wykonuje odejmowanie `CFileTimeSpan` obiektu i przypisuje wynik do bieżącego obiektu.|
|[CFileTimeSpan:: operator = =](#operator_eq_eq)|Porównuje `CFileTimeSpan` dwa obiekty pod kątem równości.|
|[CFileTimeSpan:: operator&gt;](#operator_gt)|Porównuje `CFileTimeSpan` dwa obiekty w celu określenia większego.|
|[CFileTimeSpan:: operator&gt;=](#operator_gt_eq)|Porównuje `CFileTimeSpan` dwa obiekty, aby określić równość lub większą.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia metody zarządzania względnymi okresami czasu, które często występują podczas wykonywania operacji dotyczących momentu utworzenia pliku, ostatniego dostępu lub ostatniej modyfikacji. Metody tej klasy są często używane w połączeniu z obiektami [klasy CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Przykład

Zobacz przykład dla [CFileTime:: milisekund](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime. h

##  <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Konstruktor.

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Istniejący `CFileTimeSpan` obiekt.

*nSpan*<br/>
Okres czasu (w milisekundach).

### <a name="remarks"></a>Uwagi

Obiekt można utworzyć przy użyciu istniejącego `CFileTimeSpan` obiektu lub wyrażony jako wartość 64-bitowa. `CFileTimeSpan` Domyślny konstruktor ustawia przedział czasu na 0.

##  <a name="gettimespan"></a>CFileTimeSpan:: GetTimeSpan

Wywołaj tę metodę, aby pobrać przedział czasu `CFileTimeSpan` z obiektu.

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca przedział czasu (w milisekundach).

##  <a name="operator_-"></a>CFileTimeSpan:: operator-

Wykonuje odejmowanie `CFileTimeSpan` obiektu.

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

`CFileTimeSpan` Zwraca obiekt reprezentujący wynik różnicy między dwoma przedziałami czasu.

##  <a name="operator_neq"></a>CFileTimeSpan:: operator! =

Porównuje `CFileTimeSpan` dwa obiekty pod kątem nierówności.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Obiekt `CFileTimeSpan` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli porównywany element nie jest równy `CFileTimeSpan` obiektowi; w przeciwnym razie false.

##  <a name="operator_add"></a>CFileTimeSpan:: operator +

Wykonuje Dodawanie do `CFileTimeSpan` obiektu.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

`CFileTimeSpan` Zwraca obiekt zawierający sumę dwóch przedziałów czasu.

##  <a name="operator_add_eq"></a>CFileTimeSpan:: operator + =

Wykonuje Dodawanie `CFileTimeSpan` do obiektu i przypisuje wynik do bieżącego obiektu.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiekt zawierający sumę dwóch przedziałów czasu.

##  <a name="operator_lt"></a>CFileTimeSpan:: operator&lt;

Porównuje `CFileTimeSpan` dwa obiekty, aby określić, że są one mniejsze.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Obiekt `CFileTimeSpan` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest mniejszy (czyli reprezentuje krótszy czas) niż drugi, w przeciwnym razie FALSE.

##  <a name="operator_lt_eq"></a>CFileTimeSpan:: operator&lt;=

Porównuje `CFileTimeSpan` dwa obiekty, aby określić równość lub mniejszą.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Obiekt `CFileTimeSpan` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest mniejszy niż (czyli reprezentuje krótszy czas) lub równy drugiemu, w przeciwnym razie FALSE.

##  <a name="operator_eq"></a>CFileTimeSpan:: operator =

Operator przypisania.

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiekt.

##  <a name="operator_-_eq"></a>CFileTimeSpan:: operator-=

Wykonuje odejmowanie `CFileTimeSpan` obiektu i przypisuje wynik do bieżącego obiektu.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiekt.

##  <a name="operator_eq_eq"></a>CFileTimeSpan:: operator = =

Porównuje `CFileTimeSpan` dwa obiekty pod kątem równości.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Obiekt `CFileTimeSpan` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obiekty są równe, w przeciwnym razie FALSE.

##  <a name="operator_gt"></a>CFileTimeSpan:: operator&gt;

Porównuje `CFileTimeSpan` dwa obiekty w celu określenia większego.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Obiekt `CFileTimeSpan` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest większy niż (oznacza to, że dłuższy czas) od drugiego, w przeciwnym razie FALSE.

##  <a name="operator_gt_eq"></a>CFileTimeSpan:: operator&gt;=

Porównuje `CFileTimeSpan` dwa obiekty, aby określić równość lub większą.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Obiekt `CFileTimeSpan` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest większy niż (oznacza to, że dłuższy czas) lub równy drugi, w przeciwnym razie FALSE.

##  <a name="settimespan"></a>CFileTimeSpan:: SetTimeSpan

Wywołaj tę metodę, aby ustawić przedział `CFileTimeSpan` czasu obiektu.

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan*<br/>
Nowa wartość przedziału czasu (w milisekundach).

## <a name="see-also"></a>Zobacz także

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime, klasa](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
