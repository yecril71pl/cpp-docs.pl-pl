---
title: Struktura CCreateContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CCreateContext
dev_langs: C++
helpviewer_keywords: CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 900664f43b132b118a8da0b855d5d5291fd79fee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccreatecontext-structure"></a>Struktura CCreateContext
Używa w ramach `CCreateContext` struktury podczas tworzenia okna ramowe i widoki, które są skojarzone z dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>Uwagi  
 `CCreateContext`jest to struktura i nie ma klasy podstawowej.  
  
 Podczas tworzenia okna wartości w tej strukturze Podaj informacje używane do łączenia z części dokumentu do widoku jego dane. Należy użyć `CCreateContext` jeśli są zastępowanie części procesu tworzenia.  
  
 A `CCreateContext` struktura zawiera łącza do dokumentu, okno ramowe widoku i szablonu dokumentu. Zawiera także wskaźnik do `CRuntimeClass` identyfikujący rodzaj widoku, aby utworzyć. Informacje o klasie czasu wykonywania i bieżący wskaźnik dokumentu są używane do tworzenia nowego widoku dynamicznego. Poniższa tabela zawiera sugestie sposób i czas każdego `CCreateContext` element członkowski może być używany:  
  
|Element członkowski|Typ|Co to jest|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`do tworzenia nowego widoku.|  
|`m_pCurrentDoc`|`CDocument*`|Istniejący dokument ma zostać skojarzony z nowego widoku.|  
|`m_pNewDocTemplate`|`CDocTemplate*`|Szablon dokumentu związane z tworzeniem okno ramowe MDI.|  
|`m_pLastView`|`CView*`|Oryginalnego widoku, na którym są modelowane dodatkowe widoki, jak tworzenie widoków okna podziału lub tworzenie drugi widok w dokumencie.|  
|`m_pCurrentFrame`|`CFrameWnd*`|Okno ramowe, na którym są modelowane okien ramowych dodatkowe, jak tworzenie drugie okno ramowe w dokumencie.|  
  
 Gdy szablon dokumentu tworzy dokument i jego skojarzone składniki, sprawdza poprawność informacji przechowywanych w `CCreateContext` struktury. Na przykład widoku nie można utworzyć dla nieistniejącego dokumentu.  
  
> [!NOTE]
>  Wszystkie wskaźniki w `CCreateContext` są opcjonalne i może być `NULL` nieokreślone lub nieznany.  
  
 `CCreateContext`jest używany przez funkcje Członkowskie kategorii "Zobacz też". Sprawdź opisy tych funkcji szczegółowe informacje, jeśli mają one zastąpione.  
  
 Oto kilka porad:  
  
-   Gdy przekazanego jako argument Tworzenie okna, podobnie jak w `CWnd::Create`, `CFrameWnd::Create`, i `CFrameWnd::LoadFrame`, kontekst Utwórz Określa, jakie nowym oknie powinny być podłączone do. Dla większości systemu windows, cała struktura jest opcjonalna i `NULL` można przekazać wskaźnika.  
  
-   Dla funkcji Członkowskich możliwym do zastąpienia takich jak `CFrameWnd::OnCreateClient`, `CCreateContext` argument jest opcjonalny.  
  
-   Dla funkcji Członkowskich biorących udział w widoku tworzenie, musisz podać wystarczających informacji do utworzenia widoku. Na przykład dla pierwszy widok w oknie podziału, należy podać informacje o klasie widoku i bieżącego dokumentu.  
  
 Ogólnie rzecz biorąc, jeśli używasz framework wartości domyślne, możesz zignorować `CCreateContext`. Jeśli próba zmiany bardziej zaawansowanych, Microsoft Foundation Class Library kodu źródłowego lub programy przykładowe, takie jak VIEWEX, przeprowadzi Cię. Jeśli zapomnisz wymaganego parametru potwierdzenia framework informuje co pamiętasz.  
  
 Aby uzyskać więcej informacji na temat `CCreateContext`, zobacz przykład MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [CWnd::Create](../../mfc/reference/cwnd-class.md#create)

