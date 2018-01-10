---
title: "Ostrzeżenie LNK4221 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4221
dev_langs: C++
helpviewer_keywords: LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3fb348ebb05b7af40821b4f3968a920c2e9e773
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4221"></a>Ostrzeżenie LNK4221 narzędzi konsolidatora
Ten plik obiektu nie definiuje żadnych wcześniej niezdefiniowanych symboli publicznych, więc nie będzie on używany przez żadną operację konsolidacji korzystającą z tej biblioteki  
  
 Należy wziąć pod uwagę poniższe fragmenty kodu dwa.  
  
```  
// a.cpp  
#include <atlbase.h>  
```  
  
```  
// b.cpp  
#include <atlbase.h>  
int function()  
{  
   return 0;  
}  
  
```  
  
 Aby skompilować pliki i utworzyć dwa pliki obiektu, uruchom **cl /c a.cpp b.cpp** w wierszu polecenia. W przypadku łączenia plików obiektów, uruchamiając **link/lib /out:test.lib a.obj b.obj**, zostanie wyświetlone ostrzeżenie LNK4221. Gdy łącze obiekty uruchamiając **link/lib /out:test.lib b.obj a.obj**, nie zostanie wyświetlone ostrzeżenie.  
  
 Ostrzeżenie nie jest generowane w drugim scenariuszu, ponieważ konsolidator działa w sposób w ostatniej wytworzenia. W pierwszego scenariusza b.obj jest przetwarzana przed a.obj i a.obj niemającym symboli nowy do dodania. Przez poinstruowanie konsolidator, aby najpierw przetworzyć a.obj, można uniknąć tego ostrzeżenia.  
  
 Typową przyczyną tego błędu jest po dwa pliki źródłowe określ opcję [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md) o takiej samej nazwie pliku nagłówka, określona w **Prekompilowanego nagłówka** pola. Typową przyczyną tego problemu dotyczy stdafx.h, ponieważ domyślnie stdafx.cpp obejmuje stdafx.h i nie udostępnia żadnych nowych symboli. Jeśli inny plik źródłowy zawiera stdafx.h z **/Yc** i pliku obj. skojarzony jest przetwarzana przed stdafx.obj, konsolidator zgłosi LNK4221.  
  
 Jednym ze sposobów rozwiązania tego problemu jest upewnij się, że dla każdego prekompilowanego nagłówka, istnieje tylko jeden plik źródłowy, który zawiera go przy użyciu **/Yc**. Wszystkie pliki źródłowe, należy użyć prekompilowanych nagłówków. Aby uzyskać więcej informacji na temat zmiany tego ustawienia, zobacz [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md).