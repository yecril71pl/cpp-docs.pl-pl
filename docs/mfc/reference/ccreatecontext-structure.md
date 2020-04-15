---
title: Struktura CCreateContext
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 29fc6210b9888b6a5ba5aaf15b66242c29c15dc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369382"
---
# <a name="ccreatecontext-structure"></a>Struktura CCreateContext

Struktura używa `CCreateContext` struktury podczas tworzenia okien ramki i widoków, które są skojarzone z dokumentem.

## <a name="syntax"></a>Składnia

```
struct CCreateContext
```

## <a name="remarks"></a>Uwagi

`CCreateContext`jest strukturą i nie ma klasy podstawowej.

Podczas tworzenia okna wartości w tej strukturze zawierają informacje używane do łączenia składników dokumentu z widokiem jego danych. Należy użyć `CCreateContext` tylko wtedy, gdy są nadrzędne części procesu tworzenia.

Struktura `CCreateContext` zawiera wskaźniki do dokumentu, okna ramki, widoku i szablonu dokumentu. Zawiera również wskaźnik do, `CRuntimeClass` który identyfikuje typ widoku do utworzenia. Informacje o klasie w czasie wykonywania i bieżący wskaźnik dokumentu są używane do dynamicznego tworzenia nowego widoku. W poniższej tabeli `CCreateContext` przedstawiono, jak i kiedy każdy element członkowski może być używany:

|Członek|Typ|Do czego służy|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`nowego widoku do utworzenia.|
|`m_pCurrentDoc`|`CDocument*`|Istniejący dokument, który ma być skojarzony z nowym widokiem.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Szablon dokumentu skojarzony z utworzeniem nowego okna ramki MDI.|
|`m_pLastView`|`CView*`|Oryginalny widok, na którym są modelowane dodatkowe widoki, jak podczas tworzenia widoków okna rozdzielacza lub tworzenia drugiego widoku w dokumencie.|
|`m_pCurrentFrame`|`CFrameWnd*`|Okno ramki, na którym są modelowane dodatkowe okna ramek, jak podczas tworzenia drugiego okna ramki w dokumencie.|

Gdy szablon dokumentu tworzy dokument i skojarzone z nim składniki, `CCreateContext` sprawdza poprawność informacji przechowywanych w strukturze. Na przykład widok nie powinien być tworzony dla nieistniejącego dokumentu.

> [!NOTE]
> Wszystkie wskaźniki w `CCreateContext` są opcjonalne `NULL` i może być, jeśli nieokreślone lub nieznane.

`CCreateContext`jest używany przez funkcje członkowskie wymienione w obszarze "Zobacz też". Jeśli planujesz ich zastąpić, zapoznaj się z opisami tych funkcji.

Oto kilka ogólnych wytycznych:

- Po przekazaniu jako argument do `CWnd::Create`tworzenia `CFrameWnd::Create`okna, jak w , i , kontekst `CFrameWnd::LoadFrame`tworzenia określa, co nowe okno powinno być połączone. W przypadku większości okien cała struktura `NULL` jest opcjonalna i można przekazać wskaźnik.

- Dla zastępowalnych funkcji elementów członkowskich, takich jak `CFrameWnd::OnCreateClient` `CCreateContext` argument jest opcjonalny.

- W przypadku funkcji członkowskich zaangażowanych w tworzenie widoku należy podać wystarczającą ilość informacji, aby utworzyć widok. Na przykład dla pierwszego widoku w oknie rozdzielacza należy podać informacje o klasie widoku i bieżącym dokumencie.

Ogólnie rzecz biorąc, jeśli używasz domyślnych `CCreateContext`framework, można zignorować . W przypadku próby bardziej zaawansowanych modyfikacji, kod źródłowy biblioteki klas Programu Microsoft Foundation lub przykładowe programy, takie jak VIEWEX, poprowadzą Cię. Jeśli zapomnisz wymaganego parametru, asercja struktury powie Ci, co zapomniałeś.

Aby uzyskać `CCreateContext`więcej informacji na temat , zobacz przykład MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Utwórz](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Tworzenie](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[Cwnd::create](../../mfc/reference/cwnd-class.md#create)
