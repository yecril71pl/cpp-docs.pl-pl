---
title: Błąd narzędzi konsolidatora LNK1312 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748276ed8fa459c41174f23d32bcef127cbdd510
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1312"></a>Błąd narzędzi konsolidatora LNK1312
nieprawidłowy lub uszkodzony plik: nie można zaimportować zestawu  
  
 Podczas kompilowania zestawu, plików innych niż moduł lub zestawu skompilowanego z **/CLR** został przekazany do **/assemblymodule** — opcja konsolidatora.  Jeśli przekazany plik obiektu do **/assemblymodule**, po prostu Przekaż obiekt bezpośrednio do konsolidatora, a nie do **/assemblymodule**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład utworzony plik .obj.  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK1312.  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```