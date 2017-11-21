---
title: Struktura TOOLTIPTEXT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TOOLTIPTEXT
dev_langs: C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4c0fb340f5f912cd4356be1c87bf78110a30ff7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tooltiptext-structure"></a>Struktura TOOLTIPTEXT
W przypadku pisma użytkownika [obsługi powiadamiania tip narzędzia](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), należy użyć `TOOLTIPTEXT` struktury. Elementy członkowskie `TOOLTIPTEXT` struktury są:  
  
 `typedef struct {`  
  
 `NMHDR     hdr;        // required for all WM_NOTIFY messages`  
  
 `LPTSTR    lpszText;   // see below`  
  
 `TCHAR     szText[80]; // buffer for tool tip text`  
  
 `HINSTANCE hinst;      // see below`  
  
 `UINT      uflags;     // flag indicating how to interpret the`  
  
 `// idFrom member of the NMHDR structure`  
  
 `// that is included in the structure`  
  
 `} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;`  
  
 `hdr`  
 Określa narzędzie, które wymaga tekstu. Jedynym członkiem tej struktury, który może być konieczne jest identyfikator formantu polecenia. Identyfikator polecenia formantu będą znajdować się w `idFrom` członkiem `NMHDR` struktury dostęp przy użyciu składni `hdr.idFrom`. Zobacz [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) omówienie członkami `NMHDR` struktury.  
  
 `lpszText`  
 Adres ciąg do odbierania tekstu dla narzędzia.  
  
 `szText`  
 Bufor, który odbiera tekst wskazówki. Aplikację można skopiować tekst do buforu jako alternatywę do określenia adresu ciągu.  
  
 `hinst`  
 Dojście wystąpienia, który zawiera ciąg, który ma być używany jako tekst wskazówki. Jeśli `lpszText` adres z tekst wskazówki ten element członkowski ma wartość NULL.  
  
 Podczas obsługi `TTN_NEEDTEXT` powiadomień wiadomości, podaj ciąg, który będzie wyświetlany w jednym z następujących sposobów:  
  
-   Skopiuj tekst w buforze określona przez `szText` elementu członkowskiego.  
  
-   Skopiuj adres buforu, który zawiera tekst, który `lpszText` elementu członkowskiego.  
  
-   Skopiuj identyfikator zasobu ciągu do `lpszText` — członek, a następnie skopiuj dojście wystąpienia, który zawiera zasób do `hinst` elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

