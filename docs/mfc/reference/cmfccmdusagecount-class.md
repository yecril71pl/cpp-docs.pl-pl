---
title: Klasa CMFCCmdUsageCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0db24894777170d2860ba8d1639fd44e3893732a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccmdusagecount-class"></a>Klasa CMFCCmdUsageCount
Śledzenie użycia liczba komunikatów systemu Windows, takich jak użytkownik wybrał element z menu.  
  
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
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Zwiększa o jeden licznik, który jest skojarzony z danego polecenia.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|Pobiera Licznik użycia, skojarzony z identyfikatorem danego polecenia.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Określa, czy ten obiekt zebrał minimalną ilość danych śledzenia.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Określa, czy dane polecenie są często używane.|  
|[CMFCCmdUsageCount::Reset](#reset)|Czyści Licznik użycia wszystkich poleceń.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Odczytuje obiekt z archiwum i zapisuje go do archiwum. (Przesłania [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Ustawia wartości udostępnione `CMFCCmdUsageCount` klasy elementów członkowskich danych.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`m_CmdUsage`|A `CMap` obiekt, który mapuje poleceń z liczbą ich użycia.|  
|`m_nMinUsagePercentage`|Wartość procentowa użycia minimalna polecenie, które ma być często używane.|  
|`m_nStartCount`|Licznik start, który służy do określania, czy ten obiekt zebrał minimalną ilość danych śledzenia.|  
|`m_nTotalUsage`|Liczba poleceń wszystkie śledzone.|  
  
### <a name="remarks"></a>Uwagi  
 `CMFCCmdUsageCount` Klasy mapuje każdy identyfikator numeryczny komunikatów systemu Windows na licznik 32-bitowej liczby całkowitej bez znaku. `CMFCToolBar`korzysta z tej klasy, aby wyświetlić elementy najczęściej używanych narzędzi. Aby uzyskać więcej informacji na temat `CMFCToolBar`, zobacz [CMFCToolBar klasy](../../mfc/reference/cmfctoolbar-class.md).  
  
 Można ją utrwalić `CMFCCmdUsageCount` klasy danych między uruchamia program. Użyj [CMFCCmdUsageCount::Serialize](#serialize) metody do serializowania danych elementu członkowskiego klasy i [CMFCCmdUsageCount::SetOptions](#setoptions) metodę, aby ustawić udostępnionego elementu członkowskiego danych.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 Zwiększa o jeden licznik, który jest skojarzony z danego polecenia.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`uiCmd`|Określa licznik polecenie, aby zwiększyć.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje nowy wpis do struktury mapy liczników polecenia `m_CmdUsage`, jeśli wpis nie istnieje.  
  
 Ta metoda nie działa w następujących przypadkach:  
  
-   W ramach narzędzi jest w trybie dostosowania ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) metoda zwraca wartość niezerową).  
  
-   Polecenie odwołuje się do menu lub podmenu separatora ( `uiCmd` jest równa 0 lub wartość -1).  
  
- `uiCmd`odwołuje się do poleceń standardowych (globalnej `IsStandardCommand` funkcja zwraca wartość niezerową).  
  
##  <a name="getcount"></a>CMFCCmdUsageCount::GetCount  
 Pobiera Licznik użycia, skojarzony z identyfikatorem danego polecenia.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`uiCmd`|Identyfikator polecenia licznika można pobrać.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Licznik użycia, skojarzony z identyfikatorem danego polecenia.  
  
##  <a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 Określa, czy ten obiekt odebrał minimalną ilość danych śledzenia.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ten obiekt otrzymał minimalną ilość danych; śledzenia w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość niezerową, jeśli łączna liczba `m_nTotalUsage`, wszystkie śledzone poleceń jest równa lub większa niż liczba początkowa `m_nStartCount`. Domyślnie platformę ustawia liczba początkowa 0. Tę wartość można zastąpić przy użyciu [CMFCCmdUsageCount::SetOptions](#setoptions) metody.  
  
 Ta metoda jest używana przez [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) do ustalenia, czy można wyświetlić wszystkie dostępne polecenia.  
  
##  <a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Określa, czy dane polecenie są często używane.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`uiCmd`|Określa polecenie, aby sprawdzić.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli polecenie jest często używane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość 0, jeśli użycie polecenia całkowita `m_nTotalUsage`, jest równa 0. W przeciwnym razie ta metoda zwraca wartość niezerową, jeśli wartość procentowa, którego określone polecenie jest używany jest większy niż minimalny procent `m_nMinUsagePercentage`. Domyślnie platformę Ustawia minimalny procent 5. Tę wartość można zastąpić przy użyciu [CMFCCmdUsageCount::SetOptions](#setoptions) metody. Minimalny procent w przypadku 0, ta metoda zwraca różną od zera, jeśli liczba określone polecenie jest większy niż 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) używa tej metody w celu określenia, czy polecenie jest rzadko używana.  
  
##  <a name="reset"></a>CMFCCmdUsageCount::Reset  
 Czyści Licznik użycia wszystkich poleceń.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, wyczyść wszystkie wpisy z struktury mapy liczników polecenia `m_CmdUsage`i zresetować użycia polecenia całkowita `m_nTotalUsage`, licznik na 0.  
  
##  <a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 Odczytuje obiekt z archiwum lub zapisuje go do archiwum.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`ar`|A `CArchive` obiektu do zserializowania z lub do.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wykonuje serializację struktury mapy liczników polecenia `m_CmdUsage`i użycie polecenia całkowita `m_nTotalUsage`, licznik z lub do określonego archiwum.  
  
 Serializacja przykłady można znaleźć [serializacja: serializacja obiektu](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
 Ustawia wartości udostępnione `CMFCCmdUsageCount` klasy elementów członkowskich danych.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`nStartCount`|Początkowa liczba nowych poleceń wszystkie śledzone.|  
|[in]`nMinUsagePercentage`|Nowy procent użycia minimalnej.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończy się powodzeniem, `FALSE` Jeśli `nMinUsagePercentage` parametr jest większa niż lub równa 100.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia udostępnionego `CMFCCmdUsageCount` klasy elementy członkowskie danych `m_nStartCount` i `m_nMinUsagePercentage` do `nStartCount` i `nMinUsagePercentage`odpowiednio. `m_nStartCount`jest używany przez [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) metodę, aby określić, czy ten obiekt zebrał minimalną ilość danych śledzenia. `m_nMinUsagePercentage`jest używany przez [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) metodę, aby określić, czy dane polecenie jest często używany.  
  
 W kompilacjach debugowania ta metoda generuje błąd potwierdzenia, jeśli `nMinUsagePercentage` parametr jest większa niż lub równa 100.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
