---
title: Klasa CMFCCmdUsageCount | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44172ffdf7985b7ab304e232eb03b859313df6bc
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853767"
---
# <a name="cmfccmdusagecount-class"></a>Klasa CMFCCmdUsageCount
Śledzi Licznik użycia komunikatów Windows, na przykład gdy użytkownik wybierze element menu.  
  
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
|[CMFCCmdUsageCount::GetCount](#getcount)|Pobiera Licznik użycia, który jest skojarzony z identyfikatora polecenia.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Określa, czy ten obiekt zebrał minimalnej ilości danych śledzenia.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Określa, czy dane polecenie jest często używany.|  
|[CMFCCmdUsageCount::Reset](#reset)|Czyści Licznik użycia wszystkich poleceń.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Odczytuje obiekt z archiwum lub zapisuje je do archiwum. (Przesłania [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Ustawia wartości udostępnione `CMFCCmdUsageCount` składowe danych klasy.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`m_CmdUsage`|Element `CMap` obiektu, który mapuje polecenia na ich liczniki zużycia.|  
|`m_nMinUsagePercentage`|Wartość procentowa minimalne użycie to polecenie, aby być często używane.|  
|`m_nStartCount`|Licznik rozpoczęcia, który służy do określania, czy ten obiekt zebrał minimalnej ilości danych śledzenia.|  
|`m_nTotalUsage`|Liczba poleceń wszystko można śledzić.|  
  
### <a name="remarks"></a>Uwagi  
 `CMFCCmdUsageCount` Klasy mapuje każdy identyfikator liczbowy komunikat Windows licznika 32-bitowej nieoznaczonej liczby całkowitej. `CMFCToolBar` korzysta z tej klasy, aby wyświetlić elementy najczęściej używanych narzędzi. Aby uzyskać więcej informacji na temat `CMFCToolBar`, zobacz [klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).  
  
 Jednak można utrwalić `CMFCCmdUsageCount` klasy danych między kolejnymi uruchomieniami programu. Użyj [CMFCCmdUsageCount::Serialize](#serialize) metodę, aby serializować danych składowych klasy i [CMFCCmdUsageCount::SetOptions](#setoptions) metodę, aby ustawić udostępnionej składowej danych.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>  CMFCCmdUsageCount::AddCmd  
 Zwiększa o jeden licznik, który jest skojarzony z danego polecenia.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *uiCmd*|Określa licznik polecenie, aby dodać kolejne.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje nowy wpis do struktury mapy liczb polecenia `m_CmdUsage`, jeśli wpis nie istnieje.  
  
 Ta metoda nie działa w następujących przypadkach:  
  
-   W ramach narzędzi jest w trybie dostosowywania ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) metoda zwraca wartość różną od zera).  
  
-   Polecenie odwołuje się do separator menu lub podmenu ( *uiCmd* jest równa 0 lub wartość -1).  
  
- *uiCmd* odnosi się do poleceń standardowych (globalna `IsStandardCommand` funkcja zwraca wartość różną od zera).  
  
##  <a name="getcount"></a>  CMFCCmdUsageCount::GetCount  
 Pobiera Licznik użycia, który jest skojarzony z identyfikatora polecenia.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *uiCmd*|Identyfikator licznika polecenia do pobrania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Licznik użycia, który jest skojarzony z identyfikatora polecenia.  
  
##  <a name="hasenoughinformation"></a>  CMFCCmdUsageCount::HasEnoughInformation  
 Określa, czy ten obiekt odebrał minimalnej ilości danych śledzenia.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli ten obiekt otrzymają minimalnej ilości danych; śledzenia w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość różną od zera, jeśli łączna liczba `m_nTotalUsage`, wszystko można śledzić poleceń jest równa lub większa niż liczba początkowa `m_nStartCount`. Domyślnie struktura ustawia początkowej liczby 0. Tę wartość można zastąpić za pomocą [CMFCCmdUsageCount::SetOptions](#setoptions) metody.  
  
 Ta metoda jest używana przez [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) ustalenie, czy mają być wyświetlane wszystkie dostępne polecenia.  
  
##  <a name="isfreqeuntlyusedcmd"></a>  CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Określa, czy dane polecenie jest często używany.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *uiCmd*|Określa polecenie, aby sprawdzić.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli polecenie jest często używane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość 0, jeśli użycie polecenia całkowita `m_nTotalUsage`, ma wartość 0. W przeciwnym razie ta metoda zwraca wartość różną od zera, jeśli wartość procentowa określone polecenie jest używane jest większy niż minimalny procent `m_nMinUsagePercentage`. Domyślnie struktura Ustawia minimalny procent 5. Tę wartość można zastąpić za pomocą [CMFCCmdUsageCount::SetOptions](#setoptions) metody. Jeśli minimalny procent ma wartość 0, ta metoda zwraca wartość różną od zera, jeśli liczba określone polecenie jest większa niż 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) korzystania z tej metody w celu określenia, czy polecenie jest rzadko używana.  
  
##  <a name="reset"></a>  CMFCCmdUsageCount::Reset  
 Czyści Licznik użycia wszystkich poleceń.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołać tę metodę, aby wyczyścić wszystkie wpisy od struktury mapy liczby polecenia `m_CmdUsage`i zresetować użycie polecenia całkowita `m_nTotalUsage`, licznik na 0.  
  
##  <a name="serialize"></a>  CMFCCmdUsageCount::Serialize  
 Odczytuje obiekt z archiwum lub zapisuje je do archiwum.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *ar*|Element `CArchive` obiektu do zserializowania z lub do.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wykonuje serializację struktury mapy liczb polecenia `m_CmdUsage`i użycie polecenia całkowita `m_nTotalUsage`, licznik, z lub do określonego archiwum.  
  
 Przykłady serializacji, zobacz [serializacja: serializacja obiektu](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>  CMFCCmdUsageCount::SetOptions  
 Ustawia wartości udostępnione `CMFCCmdUsageCount` składowe danych klasy.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in] *nStartCount*|Początkowa liczba nowych poleceń wszystko można śledzić.|  
|[in] *nMinUsagePercentage*|Nowe minimalnego użycia wartości procentowej.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda się powiedzie, wartość FALSE Jeśli *nMinUsagePercentage* parametru jest większy niż lub równa 100.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ustawia wspólnie `CMFCCmdUsageCount` składowe danych klasy `m_nStartCount` i `m_nMinUsagePercentage` do *nStartCount* i *nMinUsagePercentage*, odpowiednio. `m_nStartCount` jest używany przez [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) metodę pozwala ustalić, czy ten obiekt zebrał minimalnej ilości danych śledzenia. `m_nMinUsagePercentage` jest używany przez [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) metodę, aby określić, czy dane polecenie jest często używany.  
  
 W kompilacjach debugowania, ta metoda generuje błąd potwierdzenia, jeśli *nMinUsagePercentage* parametru jest większy niż lub równa 100.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
