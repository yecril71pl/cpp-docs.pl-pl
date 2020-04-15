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
ms.openlocfilehash: 1c03f0c62e508f9d00a352b71c8f3a18604e36c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367737"
---
# <a name="cmfccmdusagecount-class"></a>Klasa CMFCCmdUsageCount

Śledzi liczbę użycia komunikatów systemu Windows, na przykład gdy użytkownik wybierze element z menu.

## <a name="syntax"></a>Składnia

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Domyślny konstruktor.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Zwiększa się o jeden licznik, który jest skojarzony z danym poleceniem.|
|[CMFCCmdUsageCount::GetCount](#getcount)|Pobiera liczbę użycia skojarzoną z podanym identyfikatorem polecenia.|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Określa, czy ten obiekt zebrał minimalną ilość danych śledzenia.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Określa, czy podane polecenie jest często używane.|
|[CMFCCmdUsageCount::Reset](#reset)|Czyści liczbę użycia wszystkich poleceń.|
|[CMFCCmdUsageCount::Serialize](#serialize)|Odczytuje ten obiekt z archiwum lub zapisuje go w archiwum. (Zastępuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Ustawia wartości elementów członkowskich danych klasy udostępnionej. `CMFCCmdUsageCount`|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|`m_CmdUsage`|Obiekt, `CMap` który mapuje polecenia do ich użycia liczy.|
|`m_nMinUsagePercentage`|Minimalna wartość procentowa użycia dla polecenia, które ma być często używane.|
|`m_nStartCount`|Licznik startu, który jest używany do określenia, czy ten obiekt zebrał minimalną ilość danych śledzenia.|
|`m_nTotalUsage`|Liczba wszystkich śledzonych poleceń.|

### <a name="remarks"></a>Uwagi

Klasa `CMFCCmdUsageCount` mapuje każdy numeryczny identyfikator wiadomości systemu Windows na 32-bitowy niepodpisany licznik liczb całkowitych. `CMFCToolBar`używa tej klasy do wyświetlania często używanych elementów paska narzędzi. Aby uzyskać `CMFCToolBar`więcej informacji na temat , zobacz [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md).

Można utrwalać `CMFCCmdUsageCount` dane klasy między przebiegami programu. Użyj [METODY CMFCCmdUsageCount::Serialize](#serialize) do serializacji danych członkowskich klasy i metody [CMFCCmdUsageCount::SetOptions,](#setoptions) aby ustawić udostępnione dane członkowskie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Licznik CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmdusagecount.h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmdUsageCount::AddCmd

Zwiększa się o jeden licznik, który jest skojarzony z danym poleceniem.

```
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Uicmd*|[w] Określa licznik poleceń do przyrostu.|

### <a name="remarks"></a>Uwagi

Ta metoda dodaje nowy wpis do struktury mapy `m_CmdUsage`liczy polecenia, jeśli wpis jeszcze nie istnieje.

Ta metoda nie robi nic w następujących przypadkach:

- Struktura paska narzędzi jest w trybie dostosowywania [(CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) metoda zwraca wartość niezerową).

- Polecenie odnosi się do podmenu lub separatora menu ( *uiCmd* jest równe 0 lub -1).

- *uiCmd* odnosi się do standardowego `IsStandardCommand` polecenia (funkcja globalna zwraca wartość niezerową).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmdUsageCount::GetCount

Pobiera liczbę użycia skojarzoną z podanym identyfikatorem polecenia.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Uicmd*|[w] Identyfikator licznika poleceń do pobrania.|

### <a name="return-value"></a>Wartość zwracana

Liczba użycia skojarzona z podanym identyfikatorem polecenia.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation

Określa, czy ten obiekt otrzymał minimalną ilość danych śledzenia.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli ten obiekt otrzymał minimalną ilość danych śledzenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość niezerową, `m_nTotalUsage`jeśli całkowita liczba , ze wszystkich śledzonych `m_nStartCount`poleceń jest równa lub większa niż początkowa liczba. Domyślnie struktura ustawia początkową liczbę 0. Tę wartość można zastąpić za pomocą metody [CMFCCmdUsageCount::SetOptions.](#setoptions)

Ta metoda jest używana przez [CMFCMenuBar::IsShowAllCommands,](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) aby ustalić, czy wyświetlić wszystkie dostępne polecenia menu.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Określa, czy podane polecenie jest często używane.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Uicmd*|[w] Określa polecenie do sprawdzenia.|

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli polecenie jest często używane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość 0, `m_nTotalUsage`jeśli całkowite użycie polecenia, , wynosi 0. W przeciwnym razie ta metoda zwraca wartość niezerową, jeśli procent, którego `m_nMinUsagePercentage`używane jest określone polecenie, jest większy niż minimalna wartość procentowa. Domyślnie struktura ustawia minimalny procent na 5. Tę wartość można zastąpić za pomocą metody [CMFCCmdUsageCount::SetOptions.](#setoptions) Jeśli minimalna wartość procentowa wynosi 0, ta metoda zwraca wartość niezerową, jeśli określona liczba poleceń jest większa niż 0.

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) używa tej metody, aby ustalić, czy polecenie jest rzadko używane.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmdUsageCount::Reset

Czyści liczbę użycia wszystkich poleceń.

```
void Reset();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby wyczyścić wszystkie wpisy `m_CmdUsage`ze struktury mapy liczby `m_nTotalUsage`poleceń, i zresetować całkowite użycie polecenia, licznik do 0.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmdUsageCount::Serialize

Odczytuje ten obiekt z archiwum lub zapisuje go w archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Ar*|[w] Obiekt `CArchive` do serializacji z lub do.|

### <a name="remarks"></a>Uwagi

Ta metoda serializuje strukturę map zliczeń poleceń `m_CmdUsage`oraz `m_nTotalUsage`całkowite użycie polecenia , licznik z lub do określonego archiwum.

Aby zapoznać się z przykładami serializacji, zobacz [Serializacja: Serializacja obiektu](../../mfc/serialization-serializing-an-object.md).

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmdUsageCount::SetOptions

Ustawia wartości elementów członkowskich danych klasy udostępnionej. `CMFCCmdUsageCount`

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*nRozliczana liczba*|[w] Nowa początkowa liczba wszystkich śledzonych poleceń.|
|*nMinUsagePercentage*|[w] Nowy minimalny procent użycia.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda powiedzie się, FALSE, jeśli *parametr nMinUsagePercentage* jest większy lub równy 100.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia `CMFCCmdUsageCount` elementy `m_nStartCount` członkowskie `m_nMinUsagePercentage` danych klasy udostępnionej oraz *odpowiednio nStartCount* i *nMinUsagePercentage.* `m_nStartCount`jest używany przez [METODĘ CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) w celu określenia, czy ten obiekt zebrał minimalną ilość danych śledzenia. `m_nMinUsagePercentage`jest używany przez [METODĘ CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) w celu określenia, czy dane polecenie jest często używane.

W debugowania ta metoda generuje błąd potwierdzenia, jeśli *nMinUsagePercentage* parametr jest większy lub równy 100.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
