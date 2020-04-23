---
title: Struktura CMemoryState
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 94a2fb65a9a3030f9dc683d0eb30f476b9de1cad
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752613"
---
# <a name="cmemorystate-structure"></a>Struktura CMemoryState

Zapewnia wygodny sposób wykrywania przecieków pamięci w programie.

## <a name="syntax"></a>Składnia

```
struct CMemoryState
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Tworzy strukturę podobną do klasy, która steruje punktami kontrolnymi pamięci.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemoryState::Punkt kontrolny](#checkpoint)|Uzyskuje migawkę (punkt kontrolny) bieżącego stanu pamięci.|
|[CMemoryState::Dzaróżnienie](#difference)|Oblicza różnicę między dwoma `CMemoryState`obiektami typu .|
|[CMemoryState::DumpAllObjectsSCe](#dumpallobjectssince)|Zrzuca podsumowanie wszystkich aktualnie przydzielonych obiektów od poprzedniego punktu kontrolnego.|
|[CMemoryState::DumpStatistics](#dumpstatistics)|Drukuje statystyki alokacji `CMemoryState` pamięci dla obiektu.|

## <a name="remarks"></a>Uwagi

`CMemoryState`jest strukturą i nie ma klasy podstawowej.

"Przeciek pamięci" występuje, gdy pamięć dla obiektu jest przydzielany na stosie, ale nie cofnięto alokacji, gdy nie jest już wymagane. Takie przecieki pamięci może ostatecznie prowadzić do błędów braku pamięci. Istnieje kilka sposobów przydzielania i przydzielania pamięci w programie:

- Korzystanie z `free` rodziny funkcji z biblioteki czasu wykonywania. `malloc` / 

- Korzystanie `LocalAlloc` /  `LocalFree` z funkcji zarządzania `GlobalAlloc` /  `GlobalFree`pamięcią interfejsu API systemu Windows i .

- Za pomocą c++ **nowe** i **usuń** operatorów.

Diagnostyka `CMemoryState` pomaga tylko wykryć przecieki pamięci spowodowane, gdy pamięć przydzielona przy użyciu **nowego** operatora nie jest cofnięta przy użyciu **funkcji delete**. Pozostałe dwie grupy funkcji zarządzania pamięcią są dla programów innych niż C++, a mieszanie ich z **nowymi** i **usuwanymi** w tym samym programie nie jest zalecane. Dodatkowe makro, DEBUG_NEW, jest dostarczane w celu zastąpienia **nowego** operatora, gdy potrzebne jest śledzenie alokacji pamięci przez plik i numer wiersza. DEBUG_NEW jest używany w każdym przypadku, gdy normalnie używasz **nowego** operatora.

Podobnie jak w przypadku `CMemoryState` innych diagnostyki, diagnostyka jest dostępna tylko w wersjach debugowania programu. Wersja debugowania musi mieć zdefiniowaną stałą _DEBUG.

Jeśli podejrzewasz, że program ma przeciek `Checkpoint`pamięci, można użyć programu , `Difference`i `DumpStatistics` funkcji, aby odkryć różnicę między stanem pamięci (obiekty przydzielone) w dwóch różnych punktach wykonywania programu. Te informacje mogą być przydatne w określaniu, czy funkcja czyści wszystkie obiekty, które przydziela.

Jeśli po prostu wiedząc, gdzie występuje brak równowagi alokacji i alokacji nie zapewnia wystarczających informacji, można użyć `DumpAllObjectsSince` funkcji do zrzutu wszystkich obiektów przydzielonych od poprzedniego wywołania do `Checkpoint`. Ten zrzut pokazuje kolejność alokacji, plik źródłowy i wiersz, w którym obiekt został przydzielony (jeśli używasz DEBUG_NEW alokacji) oraz wyprowadzenie obiektu, jego adres i jego rozmiar. `DumpAllObjectsSince`wywołuje również `Dump` funkcję każdego obiektu, aby dostarczyć informacji o jego bieżącym stanie.

Aby uzyskać więcej informacji `CMemoryState` na temat używania i innych diagnostyki, zobacz [Debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Deklaracje obiektów typu `CMemoryState` i wywołania funkcji członkowskich `#if defined(_DEBUG)/#endif` powinny być nawiasem według dyrektyw. Powoduje to diagnostyki pamięci, które mają być zawarte tylko w debugowania kompilacji programu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CMemoryState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState::Punkt kontrolny

Wykonuje podsumowanie migawki pamięci i `CMemoryState` przechowuje je w tym obiekcie.

```cpp
void Checkpoint();
```

### <a name="remarks"></a>Uwagi

Funkcje `CMemoryState` członkowskie [Difference](#difference) i [DumpAllObjectsSince](#dumpallobjectssince) używają tych danych migawki.

### <a name="example"></a>Przykład

  Zobacz przykład konstruktora [CMemoryState.](#cmemorystate)

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState

Tworzy pusty `CMemoryState` obiekt, który musi być wypełniony przez [checkpoint](#checkpoint) lub [różnica](#difference) funkcji elementu członkowskiego.

```
CMemoryState();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::Dzaróżnienie

Porównuje dwa `CMemoryState` obiekty, a następnie `CMemoryState` przechowuje różnicę w tym obiekcie.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parametry

*staryPaństwo*<br/>
Stan pamięci początkowej zdefiniowany przez `CMemoryState` punkt kontrolny.

*nowyPaństwo*<br/>
Nowy stan pamięci zdefiniowany `CMemoryState` przez punkt kontrolny.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dwa stany pamięci są różne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[Punkt kontrolny](#checkpoint) musi być wywoływany dla każdego z dwóch parametrów stanu pamięci.

### <a name="example"></a>Przykład

  Zobacz przykład konstruktora [CMemoryState.](#cmemorystate)

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSCe

Wywołuje `Dump` funkcję dla wszystkich obiektów typu pochodną z klasy, `CObject` które zostały przydzielone (i są nadal przydzielane) od ostatniego wywołania punktu [kontrolnego](#checkpoint) dla tego `CMemoryState` obiektu.

```cpp
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Uwagi

Wywołanie `DumpAllObjectsSince` z niezainicjowanym `CMemoryState` obiektem zrzuci wszystkie obiekty znajdujące się obecnie w pamięci.

### <a name="example"></a>Przykład

  Zobacz przykład konstruktora [CMemoryState.](#cmemorystate)

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::DumpStatistics

Drukuje zwięzły raport `CMemoryState` statystyki pamięci z obiektu, który jest wypełniony przez funkcję elementu członkowskiego [Różnica.](#difference)

```cpp
void DumpStatistics() const;
```

### <a name="remarks"></a>Uwagi

Raport, który jest wydrukowany na urządzeniu [afxDump,](diagnostic-services.md#afxdump) pokazuje następujące informacje:

Przykładowy raport zawiera informacje na temat liczby (lub kwoty):

- wolne bloki

- normalne bloki

- Bloki CRT

- ignoruj bloki

- bloki klienta

- maksymalna pamięć używana przez program w dowolnym momencie (w bajtach)

- całkowita pamięć aktualnie używana przez program (w bajtach)

Wolne bloki to liczba bloków, których alokacja została opóźniona, jeśli `afxMemDF` została ustawiona na `delayFreeMemDF`. Aby uzyskać więcej informacji, zobacz [afxMemDF](diagnostic-services.md#afxmemdf), w sekcji "Makra i globalne MFC".

### <a name="example"></a>Przykład

  Poniższy kod należy umieścić w *projname*App.cpp. Zdefiniuj następujące zmienne globalne:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

W `InitInstance` funkcji dodaj wiersz:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Dodaj program obsługi `ExitInstance` dla funkcji i użyj następującego kodu:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Teraz można uruchomić program w trybie debugowania, aby zobaczyć dane wyjściowe `DumpStatistics` funkcji.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
