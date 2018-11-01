---
title: Struktura CCreateContext
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: dd5659e7f91e3a2a1d653b61f12323ed1ae5a9b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438964"
---
# <a name="ccreatecontext-structure"></a>Struktura CCreateContext

Środowisko wykorzystuje `CCreateContext` struktury podczas tworzenia okna ramowe i widoki, które są skojarzone z dokumentem.

## <a name="syntax"></a>Składnia

```
struct CCreateContext
```

## <a name="remarks"></a>Uwagi

`CCreateContext` jest to struktura i nie ma klasy bazowej.

Podczas tworzenia okna wartości w tej strukturze zapewniają informacje używane do łączenia składników dokumentu do widoku danych. Trzeba użyć `CCreateContext` jeśli są zastępują części procesu tworzenia.

A `CCreateContext` struktura zawiera wskaźniki do dokumentu, okno ramowe, widok i szablonu dokumentu. Zawiera ona także wskaźnik do `CRuntimeClass` określający typ widoku, aby utworzyć. Informacje o klasie czasu wykonywania i bieżący wskaźnik dokumentu są używane do tworzenie nowego widoku dynamicznego. Poniższa tabela sugeruje, jak i kiedy każdego `CCreateContext` element członkowski może być używany:

|Element członkowski|Typ|Co to jest|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` Aby utworzyć nowego widoku.|
|`m_pCurrentDoc`|`CDocument*`|Istniejący dokument ma zostać skojarzony z nowego widoku.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Szablon dokumentu, związane z tworzeniem nowe okno ramek MDI.|
|`m_pLastView`|`CView*`|Widok oryginalnej, na którym są modelowane dodatkowe widoki, jak tworzenie widoków okno rozdzielacza lub Tworzenie drugiego widoku do dokumentu.|
|`m_pCurrentFrame`|`CFrameWnd*`|Okno ramki, na którym są modelowane dodatkowe okna ramowe, jak tworzenie drugiego okna ramki dokumentu.|

Gdy szablon dokumentu tworzy dokument i powiązanych z nim składników, sprawdza poprawność informacji przechowywanych w `CCreateContext` struktury. Na przykład widoku nie można utworzyć dla nieistniejącego dokumentu.

> [!NOTE]
>  Wszystkie wskaźniki w `CCreateContext` są opcjonalne i może być `NULL` nieokreślony lub nieznany.

`CCreateContext` jest używany przez funkcje składowe wyświetlane w obszarze "Zobacz też". Skonsultuj się opisy tych funkcji, aby uzyskać szczegółowe informacje, czy chcesz je zastąpić.

Poniżej przedstawiono kilka ogólnych wytycznych:

- Jeśli przekazywany jako argument do tworzenia okna, podobnie jak w `CWnd::Create`, `CFrameWnd::Create`, i `CFrameWnd::LoadFrame`, kontekstu Utwórz Określa, jakie nowe okno powinny być połączone. Dla większości systemów windows, cała struktura jest opcjonalna i `NULL` wskaźnika, które mogą być przekazywane.

- Dla funkcji składowych możliwym do zastąpienia takie jak `CFrameWnd::OnCreateClient`, `CCreateContext` argument jest opcjonalny.

- Dla funkcji składowej biorących udział w widoku tworzenia, musisz podać wystarczających informacji do utworzenia widoku. Na przykład pierwszy widoku okna rozdzielacza musisz podać informacje o klasie widok i w bieżącym dokumencie.

Ogólnie rzecz biorąc, korzystając z ustawień domyślnych framework, możesz zignorować `CCreateContext`. Jeśli spróbujesz bardziej zaawansowane modyfikacje, kod źródłowy biblioteki klas Microsoft Foundation lub przykładowych programów, takich jak VIEWEX, pomocne. Jeśli nie pamiętasz wymaganego parametru asercję framework informuje użytkownik zapomniał.

Aby uzyskać więcej informacji na temat `CCreateContext`, zobacz przykładową MFC [VIEWEX](../../visual-cpp-samples.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)

