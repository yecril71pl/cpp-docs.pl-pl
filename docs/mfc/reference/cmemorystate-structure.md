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
ms.openlocfilehash: a110e1345cb970c117de125bd8105e1bc86eaf94
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420688"
---
# <a name="cmemorystate-structure"></a>CMemoryState, struktura

Zapewnia wygodny sposób wykrywania przecieków pamięci w programie.

## <a name="syntax"></a>Składnia

```
struct CMemoryState
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Tworzy strukturę podobną do klasy, która kontroluje punkty kontrolne pamięci.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMemoryState:: Checkpoint](#checkpoint)|Uzyskuje migawkę (punkt kontrolny) bieżącego stanu pamięci.|
|[CMemoryState::D ifference](#difference)|Oblicza różnicę między dwoma obiektami typu `CMemoryState`.|
|[CMemoryState::D umpAllObjectsSince](#dumpallobjectssince)|Zrzuca podsumowanie wszystkich aktualnie przyznanych obiektów od ostatniego punktu kontrolnego.|
|[CMemoryState::D umpStatistics](#dumpstatistics)|Drukuje statystyki alokacji pamięci dla obiektu `CMemoryState`.|

## <a name="remarks"></a>Uwagi

`CMemoryState` jest strukturą i nie ma klasy bazowej.

"Wyciek pamięci" występuje, gdy pamięć dla obiektu jest przydzielana na stercie, ale bez cofania przydziału, gdy nie jest już wymagany. Takie przecieki pamięci mogą ostatecznie prowadzić do błędów braku pamięci. Istnieje kilka sposobów przydzielenia i cofnięcia przydziału pamięci w programie:

- Korzystanie z `malloc`/ `free` rodzinie funkcji z biblioteki wykonawczej.

- Korzystając z funkcji zarządzania pamięcią interfejsu API systemu Windows, `LocalAlloc`/ `LocalFree` i `GlobalAlloc`/ `GlobalFree`.

- Korzystanie z C++ operatorów **New** i **delete** .

Diagnostyka `CMemoryState` pomaga wykrywać przecieki pamięci w przypadku, gdy pamięć przydzieloną przy użyciu operatora **New** nie zostanie cofnięta przy użyciu polecenia **delete**. Pozostałe dwie grupy funkcji zarządzania pamięcią są przeznaczone dlaC++ programów innych niż programy i mieszanie ich przy użyciu **nowych** i **usuniętych** w tym samym programie nie są zalecane. Dodatkowe makro, DEBUG_NEW, jest dostarczane w celu zastąpienia operatora **New** , gdy potrzebujesz śledzenia plików i wierszy w wierszu. DEBUG_NEW jest używana zawsze, gdy normalnie korzystasz z operatora **New** .

Podobnie jak w przypadku innych diagnostyki, Diagnostyka `CMemoryState` jest dostępna tylko w wersjach debugowania programu. Wersja do debugowania musi mieć zdefiniowaną _DEBUG stałą.

Jeśli podejrzewasz, że program ma przeciek pamięci, możesz użyć funkcji `Checkpoint`, `Difference`i `DumpStatistics`, aby poznać różnicę między stanem pamięci (przydzielonymi obiektami) w dwóch różnych punktach w trakcie wykonywania programu. Te informacje mogą być przydatne podczas ustalania, czy funkcja czyści wszystkie obiekty, do których jest przydzielana.

Jeśli po prostu wiedzą, gdzie występuje nierównoważność alokacji i cofania alokacji, nie zapewnia wystarczającej ilości informacji, możesz użyć funkcji `DumpAllObjectsSince`, aby zrzucić wszystkie obiekty przydzielone od czasu poprzedniego wywołania do `Checkpoint`. Ten zrzut przedstawia kolejność alokacji, plik źródłowy i wiersz, w którym został przydzielony obiekt (Jeśli używasz DEBUG_NEW do alokacji), a następnie wyprowadzanie obiektu, jego adresu i jego rozmiaru. `DumpAllObjectsSince` również wywołuje funkcję `Dump` każdego obiektu, aby podać informacje o jego bieżącym stanie.

Aby uzyskać więcej informacji o sposobach korzystania z `CMemoryState` i innych danych diagnostycznych, zobacz [debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Deklaracje obiektów typu `CMemoryState` i wywołania funkcji Członkowskich należy przenawiasować według dyrektywy `#if defined(_DEBUG)/#endif`. Powoduje to, że Diagnostyka pamięci jest uwzględniana tylko w kompilacjach debugowania programu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CMemoryState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="checkpoint"></a>CMemoryState:: Checkpoint

Wykonuje podsumowanie migawek pamięci i zapisuje je w tym obiekcie `CMemoryState`.

```
void Checkpoint();
```

### <a name="remarks"></a>Uwagi

`CMemoryState` [różnice](#difference) w funkcjach składowych i [DumpAllObjectsSince](#dumpallobjectssince) używać tych danych migawki.

### <a name="example"></a>Przykład

  Zobacz przykład dla konstruktora [CMemoryState](#cmemorystate) .

##  <a name="cmemorystate"></a>CMemoryState::CMemoryState

Konstruuje pusty obiekt `CMemoryState`, który musi zostać wypełniony przez [punkt kontrolny](#checkpoint) lub funkcję składową [różnic](#difference) .

```
CMemoryState();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>CMemoryState::D ifference

Porównuje dwa `CMemoryState` obiektów, a następnie przechowuje różnicę w tym obiekcie `CMemoryState`.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parametry

*oldState*<br/>
Początkowy stan pamięci określony przez punkt kontrolny `CMemoryState`.

*newState*<br/>
Nowy stan pamięci określony przez punkt kontrolny `CMemoryState`.

### <a name="return-value"></a>Wartość zwrócona

Wartość różna od zera, jeśli dwa stany pamięci są różne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[Punkt kontrolny](#checkpoint) musi zostać wywołany dla każdego z dwóch parametrów stanu pamięci.

### <a name="example"></a>Przykład

  Zobacz przykład dla konstruktora [CMemoryState](#cmemorystate) .

##  <a name="dumpallobjectssince"></a>CMemoryState::D umpAllObjectsSince

Wywołuje funkcję `Dump` dla wszystkich obiektów typu pochodzącego od klasy `CObject`, które zostały przydzieloną (i nadal są przydzieleni) od momentu ostatniego wywołania [punktu kontrolnego](#checkpoint) dla tego obiektu `CMemoryState`.

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Uwagi

Wywołanie `DumpAllObjectsSince` z niezainicjowanym obiektem `CMemoryState` spowoduje zrzut wszystkich obiektów znajdujących się obecnie w pamięci.

### <a name="example"></a>Przykład

  Zobacz przykład dla konstruktora [CMemoryState](#cmemorystate) .

##  <a name="dumpstatistics"></a>CMemoryState::D umpStatistics

Drukuje zwięzły raport statystyk pamięci z obiektu `CMemoryState`, który jest wypełniany przez funkcję składową [różnic](#difference) .

```
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

Bloki bezpłatne to liczba bloków, których cofnięcie przydziału zostało opóźnione, jeśli `afxMemDF` została ustawiona na `delayFreeMemDF`. Aby uzyskać więcej informacji, zobacz [afxMemDF](diagnostic-services.md#afxmemdf), w sekcji "makra MFC i Globals".

### <a name="example"></a>Przykład

  Poniższy kod powinien zostać umieszczony w programie *Projname*App. cpp. Zdefiniuj następujące zmienne globalne:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

W funkcji `InitInstance` Dodaj wiersz:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Dodaj program obsługi dla funkcji `ExitInstance` i użyj następującego kodu:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Teraz można uruchomić program w trybie debugowania, aby wyświetlić dane wyjściowe funkcji `DumpStatistics`.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
