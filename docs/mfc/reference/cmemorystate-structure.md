---
title: CMemoryState, struktura
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 823d424620e205d14f247a147bbf7dcb40a626b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222917"
---
# <a name="cmemorystate-structure"></a>CMemoryState, struktura

Zapewnia wygodny sposób wykrywania przecieków pamięci w programie.

## <a name="syntax"></a>Składnia

```
struct CMemoryState
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Tworzy strukturę podobną do klasy, która kontroluje punkty kontrolne pamięci.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemoryState:: Checkpoint](#checkpoint)|Uzyskuje migawkę (punkt kontrolny) bieżącego stanu pamięci.|
|[CMemoryState::D ifference](#difference)|Oblicza różnicę między dwoma obiektami typu `CMemoryState` .|
|[CMemoryState::D umpAllObjectsSince](#dumpallobjectssince)|Zrzuca podsumowanie wszystkich aktualnie przyznanych obiektów od ostatniego punktu kontrolnego.|
|[CMemoryState::D umpStatistics](#dumpstatistics)|Drukuje statystyki alokacji pamięci dla `CMemoryState` obiektu.|

## <a name="remarks"></a>Uwagi

`CMemoryState`jest strukturą i nie ma klasy bazowej.

"Wyciek pamięci" występuje, gdy pamięć dla obiektu jest przydzielana na stercie, ale bez cofania przydziału, gdy nie jest już wymagany. Takie przecieki pamięci mogą ostatecznie prowadzić do błędów braku pamięci. Istnieje kilka sposobów przydzielenia i cofnięcia przydziału pamięci w programie:

- Korzystanie z `malloc` /  `free` rodziny funkcji z biblioteki wykonawczej.

- Korzystanie z funkcji zarządzania pamięcią interfejsu API systemu Windows `LocalAlloc` /  `LocalFree` i `GlobalAlloc` /  `GlobalFree` .

- Używanie języka C++ **`new`** i **`delete`** operatorów.

`CMemoryState`Diagnostyka wykrywa jedynie przecieki pamięci, gdy **`new`** nie cofnięto przydziału pamięci przydzieloną przy użyciu operatora **`delete`** . Pozostałe dwie grupy funkcji zarządzania pamięcią są przeznaczone dla programów innych niż C + + i mieszanie ich z **`new`** i **`delete`** w tym samym programie nie są zalecane. Dodatkowe makro, DEBUG_NEW, jest dostarczane w celu zastąpienia **`new`** operatora, gdy potrzebujesz śledzenia plików i numerów wierszy. DEBUG_NEW jest używana zawsze, gdy normalnie korzystasz z **`new`** operatora.

Podobnie jak w przypadku innych diagnostyki, `CMemoryState` Diagnostyka jest dostępna tylko w wersji debugowej programu. Wersja do debugowania musi mieć zdefiniowaną _DEBUG stałą.

Jeśli podejrzewasz, że program ma przeciek pamięci, możesz użyć `Checkpoint` `Difference` funkcji, i, `DumpStatistics` Aby poznać różnicę między stanem pamięci (przydzielonymi obiektami) w dwóch różnych punktach w trakcie wykonywania programu. Te informacje mogą być przydatne podczas ustalania, czy funkcja czyści wszystkie obiekty, do których jest przydzielana.

Jeśli po prostu wiedzą, gdzie występuje nierównoważność alokacji i cofania alokacji, nie zapewnia wystarczającej ilości informacji, możesz użyć `DumpAllObjectsSince` funkcji, aby zrzucić wszystkie obiekty przydzielone od czasu poprzedniego wywołania do `Checkpoint` . Ten zrzut przedstawia kolejność alokacji, plik źródłowy i wiersz, w którym został przydzielony obiekt (Jeśli używasz DEBUG_NEW do alokacji), a następnie wyprowadzanie obiektu, jego adresu i jego rozmiaru. `DumpAllObjectsSince`wywołuje również funkcję każdego obiektu `Dump` , aby podać informacje o jego bieżącym stanie.

Aby uzyskać więcej informacji o sposobach korzystania z programu `CMemoryState` i innych danych diagnostycznych, zobacz [debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Deklaracje obiektów typu `CMemoryState` i wywołań do funkcji składowych powinny zostać ujęte w nawiasy klamrowe `#if defined(_DEBUG)/#endif` . Powoduje to, że Diagnostyka pamięci jest uwzględniana tylko w kompilacjach debugowania programu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CMemoryState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState:: Checkpoint

Wykonuje podsumowanie migawek pamięci i zapisuje je w tym `CMemoryState` obiekcie.

```cpp
void Checkpoint();
```

### <a name="remarks"></a>Uwagi

`CMemoryState` [Różnice](#difference) w funkcjach składowych i [DumpAllObjectsSince](#dumpallobjectssince) używają tego danych migawki.

### <a name="example"></a>Przykład

  Zobacz przykład dla konstruktora [CMemoryState](#cmemorystate) .

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState

Konstruuje pusty `CMemoryState` obiekt, który musi zostać wypełniony przez [punkt kontrolny](#checkpoint) lub funkcję składową [różnic](#difference) .

```
CMemoryState();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::D ifference

Porównuje dwa `CMemoryState` obiekty, a następnie przechowuje różnicę w tym `CMemoryState` obiekcie.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parametry

*oldState*<br/>
Początkowy stan pamięci określony przez `CMemoryState` punkt kontrolny.

*newState*<br/>
Nowy stan pamięci określony przez `CMemoryState` punkt kontrolny.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli dwa stany pamięci są różne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[Punkt kontrolny](#checkpoint) musi zostać wywołany dla każdego z dwóch parametrów stanu pamięci.

### <a name="example"></a>Przykład

  Zobacz przykład dla konstruktora [CMemoryState](#cmemorystate) .

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::D umpAllObjectsSince

Wywołuje `Dump` funkcję dla wszystkich obiektów typu pochodzącego od klasy `CObject` , które zostały przydzieloną (i nadal są przydzieleni) od momentu ostatniego wywołania [punktu kontrolnego](#checkpoint) dla tego `CMemoryState` obiektu.

```cpp
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Uwagi

Wywołanie `DumpAllObjectsSince` z niezainicjowanym `CMemoryState` obiektem spowoduje zrzut wszystkich obiektów znajdujących się obecnie w pamięci.

### <a name="example"></a>Przykład

  Zobacz przykład dla konstruktora [CMemoryState](#cmemorystate) .

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::D umpStatistics

Drukuje zwięzły raport statystyk pamięci z `CMemoryState` obiektu, który jest wypełniony przez funkcję elementu członkowskiego [różnic](#difference) .

```cpp
void DumpStatistics() const;
```

### <a name="remarks"></a>Uwagi

Raport, który jest drukowany na urządzeniu [afxDump](diagnostic-services.md#afxdump) , zawiera następujące elementy:

Przykładowy raport zawiera informacje o liczbie (lub wielkości):

- bloki bezpłatne

- bloki normalne

- Bloki CRT

- Ignoruj bloki

- bloki klienta

- Maksymalna ilość pamięci używana przez program w dowolnym momencie (w bajtach)

- Całkowita ilość pamięci używana obecnie przez program (w bajtach)

Bloki bezpłatne to liczba bloków, których cofnięcie przydziału zostało opóźnione, jeśli `afxMemDF` ustawiono wartość `delayFreeMemDF` . Aby uzyskać więcej informacji, zobacz [afxMemDF](diagnostic-services.md#afxmemdf), w sekcji "makra MFC i Globals".

### <a name="example"></a>Przykład

  Poniższy kod powinien zostać umieszczony w programie *Projname*App. cpp. Zdefiniuj następujące zmienne globalne:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

W `InitInstance` funkcji Dodaj wiersz:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Dodaj program obsługi dla `ExitInstance` funkcji i użyj następującego kodu:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Teraz można uruchomić program w trybie debugowania, aby wyświetlić dane wyjściowe `DumpStatistics` funkcji.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
