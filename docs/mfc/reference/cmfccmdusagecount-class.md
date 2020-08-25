---
title: Klasa CMFCCmdUsageCount
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: 95dca548856510cd8b06914932cc46435c28399d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834280"
---
# <a name="cmfccmdusagecount-class"></a>Klasa CMFCCmdUsageCount

Śledzi liczbę użycia komunikatów systemu Windows, na przykład gdy użytkownik wybierze element z menu.

## <a name="syntax"></a>Składnia

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Konstruktor domyślny.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Zwiększa się o jeden licznik, który jest skojarzony z danym poleceniem.|
|[CMFCCmdUsageCount:: GetCount](#getcount)|Pobiera liczbę użycia skojarzoną z danym IDENTYFIKATORem polecenia.|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Określa, czy ten obiekt zgromadził minimalną ilość danych śledzenia.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Określa, czy dostarczone polecenie jest często używane.|
|[CMFCCmdUsageCount:: Reset](#reset)|Czyści licznik użycia wszystkich poleceń.|
|[CMFCCmdUsageCount:: serializować](#serialize)|Odczytuje ten obiekt z archiwum lub zapisuje je w archiwum. (Przesłania [CObject:: serializować](../../mfc/reference/cobject-class.md#serialize)).|
|[CMFCCmdUsageCount:: Set— opcje](#setoptions)|Ustawia wartości `CMFCCmdUsageCount` elementów członkowskich danych klasy udostępnionej.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|`m_CmdUsage`|`CMap`Obiekt, który mapuje polecenia na ich liczniki użycia.|
|`m_nMinUsagePercentage`|Minimalny procent użycia dla polecenia, które ma być często używane.|
|`m_nStartCount`|Licznik początkowy, który służy do określenia, czy ten obiekt zgromadził minimalną ilość danych śledzenia.|
|`m_nTotalUsage`|Liczba wszystkich śledzonych poleceń.|

### <a name="remarks"></a>Uwagi

`CMFCCmdUsageCount`Klasa mapuje każdy liczbowy Identyfikator komunikatu systemu Windows na 32-bitową liczbę całkowitą bez znaku. `CMFCToolBar` używa tej klasy do wyświetlania często używanych elementów paska narzędzi. Aby uzyskać więcej informacji na temat `CMFCToolBar` , zobacz [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).

Można utrwalać `CMFCCmdUsageCount` dane klas między uruchomieniami programu. Użyj metody [CMFCCmdUsageCount:: serializować](#serialize) , aby serializować dane elementu członkowskiego klasy i metodę [CMFCCmdUsageCount:: SetOptions](#setoptions) , aby ustawić udostępnione dane elementu członkowskiego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmdusagecount. h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a> CMFCCmdUsageCount::AddCmd

Zwiększa się o jeden licznik, który jest skojarzony z danym poleceniem.

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*\
podczas Określa licznik poleceń do zwiększenia.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje nowy wpis do struktury mapy liczników poleceń, `m_CmdUsage` , Jeśli wpis jeszcze nie istnieje.

Ta metoda nie wykonuje żadnych działań w następujących przypadkach:

- Struktura paska narzędzi jest w trybie dostosowywania (Metoda [CMFCToolBar::](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) iscustomizationmode zwraca wartość różną od zera).

- Polecenie odnosi się do podmenu lub separatora menu ( *uiCmd* jest równe 0 lub-1).

- *uiCmd* odwołuje się do standardowego polecenia (funkcja globalna `IsStandardCommand` zwraca wartość różną od zera).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a> CMFCCmdUsageCount:: GetCount

Pobiera liczbę użycia skojarzoną z danym IDENTYFIKATORem polecenia.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

*uiCmd*\
podczas Identyfikator licznika poleceń do pobrania.

### <a name="return-value"></a>Wartość zwracana

Liczba użycia skojarzona z danym IDENTYFIKATORem polecenia.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a> CMFCCmdUsageCount::HasEnoughInformation

Określa, czy ten obiekt otrzymał minimalną ilość danych śledzenia.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli ten obiekt otrzymał minimalną ilość danych śledzenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość różną od zera, jeśli łączna liczba `m_nTotalUsage` wszystkich śledzonych poleceń jest równa lub większa od liczby początkowej `m_nStartCount` . Domyślnie struktura ustawia liczbę początkową 0. Tę wartość można zastąpić za pomocą metody [CMFCCmdUsageCount:: SetOptions](#setoptions) .

Ta metoda jest używana przez [CMFCMenuBar:: IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) , aby określić, czy mają być pokazywane wszystkie dostępne polecenia menu.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a> CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Określa, czy dostarczone polecenie jest często używane.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

*uiCmd*\
podczas Określa polecenie do sprawdzenia.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli polecenie jest często używane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość 0, jeśli całkowite użycie poleceń, `m_nTotalUsage` ma wartość 0. W przeciwnym razie ta metoda zwraca wartość różną od zera, jeśli wartość procentowa użytego polecenia jest większa niż minimalna wartość procentowa `m_nMinUsagePercentage` . Domyślnie architektura ustawia wartość procentową minimalną na 5. Tę wartość można zastąpić za pomocą metody [CMFCCmdUsageCount:: SetOptions](#setoptions) . Jeśli minimalna wartość procentowa to 0, ta metoda zwraca wartość różną od zera, jeśli określona liczba poleceń jest większa od 0.

[CMFCToolBar:: IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) korzysta z tej metody, aby określić, czy polecenie jest rzadko używane.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a> CMFCCmdUsageCount:: Reset

Czyści licznik użycia wszystkich poleceń.

```cpp
void Reset();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wyczyścić wszystkie wpisy ze struktury mapy liczników poleceń, `m_CmdUsage` i aby zresetować całkowite użycie polecenia, na `m_nTotalUsage` przykład licznik na 0.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a> CMFCCmdUsageCount:: serializować

Odczytuje ten obiekt z archiwum lub zapisuje je w archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*\
podczas `CArchive` Obiekt do serializacji z lub do.

### <a name="remarks"></a>Uwagi

Ta metoda serializacji strukturę mapy liczby poleceń, `m_CmdUsage` oraz całkowite użycie poleceń, `m_nTotalUsage` licznik z lub do określonego archiwum.

Aby zapoznać się z przykładami serializacji, zobacz [serializacji: serializacji obiektu](../../mfc/serialization-serializing-an-object.md).

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a> CMFCCmdUsageCount:: Set— opcje

Ustawia wartości `CMFCCmdUsageCount` elementów członkowskich danych klasy udostępnionej.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Parametry

*nStartCount*\
podczas Nowa początkowa liczba wszystkich śledzonych poleceń.

*nMinUsagePercentage*\
podczas Nowy minimalny procent użycia.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda powiedzie się, wartość FALSE, jeśli parametr *nMinUsagePercentage* jest większy lub równy 100.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia `CMFCCmdUsageCount` elementy członkowskie danych klasy udostępnionej `m_nStartCount` oraz `m_nMinUsagePercentage` odpowiednio do *nStartCount* i *nMinUsagePercentage*. `m_nStartCount` jest używany przez metodę [CMFCCmdUsageCount:: HasEnoughInformation](#hasenoughinformation) , aby określić, czy ten obiekt zgromadził minimalną ilość danych śledzenia. `m_nMinUsagePercentage` jest używany przez metodę [CMFCCmdUsageCount:: IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) , aby określić, czy dana polecenie jest często używane.

W programie kompilacje debugowania ta metoda generuje błąd potwierdzenia, jeśli parametr *nMinUsagePercentage* jest większy lub równy 100.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
