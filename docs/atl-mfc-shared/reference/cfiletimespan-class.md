---
title: CFileTimeSpan, klasa
ms.date: 01/06/2020
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
ms.openlocfilehash: 9220ed8373e78db727b43ecb59880dcfbcc98f96
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755055"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan, klasa

Ta klasa zapewnia metody zarządzania względnymi wartościami daty i godziny skojarzonych z plikiem.

## <a name="syntax"></a>Składnia

```cpp
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
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Wywołaj tę metodę, aby pobrać przedział czasu z obiektu `CFileTimeSpan`.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Wywołaj tę metodę, aby ustawić przedział czasu obiektu `CFileTimeSpan`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan:: operator-](#operator_-)|Wykonuje odejmowanie obiektu `CFileTimeSpan`.|
|[CFileTimeSpan:: operator! =](#operator_neq)|Porównuje dwa obiekty `CFileTimeSpan` pod kątem nierówności.|
|[CFileTimeSpan:: operator +](#operator_add)|Wykonuje Dodawanie na obiekcie `CFileTimeSpan`.|
|[CFileTimeSpan:: operator + =](#operator_add_eq)|Wykonuje Dodawanie do obiektu `CFileTimeSpan` i przypisuje wynik do bieżącego obiektu.|
|[CFileTimeSpan:: operator &lt;](#operator_lt)|Porównuje dwa obiekty `CFileTimeSpan`, aby określić, że są one mniejsze.|
|[CFileTimeSpan:: operator &lt;=](#operator_lt_eq)|Porównuje dwa obiekty `CFileTimeSpan`, aby określić równość lub mniejszą.|
|[CFileTimeSpan:: operator =](#operator_eq)|Operator przypisania.|
|[CFileTimeSpan:: operator-=](#operator_-_eq)|Wykonuje odejmowanie obiektu `CFileTimeSpan` i przypisuje wynik do bieżącego obiektu.|
|[CFileTimeSpan:: operator = =](#operator_eq_eq)|Porównuje dwa obiekty `CFileTimeSpan` dla równości.|
|[CFileTimeSpan:: operator &gt;](#operator_gt)|Porównuje dwa obiekty `CFileTimeSpan`, aby określić większe.|
|[CFileTimeSpan:: operator &gt;=](#operator_gt_eq)|Porównuje dwa obiekty `CFileTimeSpan`, aby określić równość lub większą.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza metody do obsługi względnych okresów czasu w jednostkach używanych przez system plików. Te jednostki są często używane w operacjach dotyczących czasu utworzenia pliku, ostatniego dostępu lub ostatniej modyfikacji. Metody tej klasy są często używane w połączeniu z obiektami [klasy CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Przykład

Zobacz przykład dla [CFileTime:: milisekund](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime. h

## <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Konstruktor.

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Istniejący obiekt `CFileTimeSpan`.

*nSpan*\
Okres czasu (w milisekundach).

### <a name="remarks"></a>Uwagi

Obiekt `CFileTimeSpan` można utworzyć przy użyciu istniejącego obiektu `CFileTimeSpan` lub wyrażony jako wartość 64-bitowa. Domyślny konstruktor ustawia przedział czasu na 0.

## <a name="gettimespan"></a>CFileTimeSpan:: GetTimeSpan

Wywołaj tę metodę, aby pobrać przedział czasu z obiektu `CFileTimeSpan`.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca przedział czasu (w milisekundach).

## <a name="operator_-"></a>CFileTimeSpan:: operator-

Wykonuje odejmowanie obiektu `CFileTimeSpan`.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt `CFileTimeSpan` reprezentujący wynik różnicy między dwoma przedziałami czasu.

## <a name="operator_neq"></a>CFileTimeSpan:: operator! =

Porównuje dwa obiekty `CFileTimeSpan` pod kątem nierówności.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Obiekt `CFileTimeSpan`, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany element nie jest równy obiektowi `CFileTimeSpan`; w przeciwnym razie FALSE.

## <a name="operator_add"></a>CFileTimeSpan:: operator +

Wykonuje Dodawanie na obiekcie `CFileTimeSpan`.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt `CFileTimeSpan` zawierający sumę dwóch przedziałów czasu.

## <a name="operator_add_eq"></a>CFileTimeSpan:: operator + =

Wykonuje Dodawanie na obiekcie `CFileTimeSpan` i przypisuje wynik do bieżącego obiektu.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany obiekt `CFileTimeSpan` zawierający sumę dwóch przedziałów czasu.

## <a name="operator_lt"></a>CFileTimeSpan:: operator &lt;

Porównuje dwa obiekty `CFileTimeSpan`, aby określić, że są one mniejsze.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Obiekt `CFileTimeSpan`, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest mniejszy (czyli reprezentuje krótszy czas) niż drugi, w przeciwnym razie FALSE.

## <a name="operator_lt_eq"></a>CFileTimeSpan:: operator &lt;=

Porównuje dwa obiekty `CFileTimeSpan`, aby określić równość lub mniejszą.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Obiekt `CFileTimeSpan`, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest mniejszy niż (czyli reprezentuje krótszy czas) lub równy drugiemu, w przeciwnym razie FALSE.

## <a name="operator_eq"></a>CFileTimeSpan:: operator =

Operator przypisania.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany obiekt `CFileTimeSpan`.

## <a name="operator_-_eq"></a>CFileTimeSpan:: operator-=

Wykonuje odejmowanie obiektu `CFileTimeSpan` i przypisuje wynik do bieżącego obiektu.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany obiekt `CFileTimeSpan`.

## <a name="operator_eq_eq"></a>CFileTimeSpan:: operator = =

Porównuje dwa obiekty `CFileTimeSpan` dla równości.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Obiekt `CFileTimeSpan`, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obiekty są równe, w przeciwnym razie FALSE.

## <a name="operator_gt"></a>CFileTimeSpan:: operator &gt;

Porównuje dwa obiekty `CFileTimeSpan`, aby określić większe.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Obiekt `CFileTimeSpan`, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest większy niż (oznacza to, że dłuższy czas) od drugiego, w przeciwnym razie FALSE.

## <a name="operator_gt_eq"></a>CFileTimeSpan:: operator &gt;=

Porównuje dwa obiekty `CFileTimeSpan`, aby określić równość lub większą.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*\
Obiekt `CFileTimeSpan`, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli pierwszy obiekt jest większy niż (oznacza to, że dłuższy czas) lub równy drugi, w przeciwnym razie FALSE.

## <a name="settimespan"></a>CFileTimeSpan:: SetTimeSpan

Wywołaj tę metodę, aby ustawić przedział czasu obiektu `CFileTimeSpan`.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan*\
Nowa wartość przedziału czasu w jednostkach 100-nanosekund. Aby uzyskać więcej informacji, zobacz [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Zobacz także

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[Klasa CFileTime](cfiletime-class.md)\
\ [wykresu hierarchii](../../mfc/hierarchy-chart.md)
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
