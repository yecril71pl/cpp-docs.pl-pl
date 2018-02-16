---
title: -CLRHEADER | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73f68c4f73d132254ea64d4b3b3b9f787f3a4b82
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="clrheader"></a>/CLRHEADER
```  
/CLRHEADER file  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 `file`  
 Skompilowany plik obrazu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="remarks"></a>Uwagi  
 CLRHEADER wyświetla informacji o nagłówkach .NET używane w programach zarządzanych. Dane wyjściowe zawierają lokalizację i rozmiar w bajtach nagłówka .NET i sekcji w nagłówku.  
  
 Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.  
  
 Gdy /CLRHEADER jest używany w pliku, który został skompilowany z/CLR, można **clr nagłówka:** sekcji w danych wyjściowych polecenia dumpbin.  Wartość **flagi** wskazuje użyto opcji/CLR:  
  
-   0 — / CLR (obraz może zawierać kod natywny).  
  
 Można również programowane sprawdzanie, jeśli obraz został utworzony dla środowiska CLR.  Aby uzyskać więcej informacji, zobacz [porady: ustalić, czy obraz jest natywnym, czy CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015 i zostanie usunięta w przyszłej wersji kompilatora. Kod, który musi być "czysty" lub "bezpiecznej" powinny być przenoszone do języka C#. 
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)