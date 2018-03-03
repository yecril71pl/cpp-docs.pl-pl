---
title: 'Porady: pobieranie wersji programu .NET Framework (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework, version
- Version property, retrieving .NET Framework version
ms.assetid: fc786fbc-c915-4b15-bcad-0d68cf2c44bd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 343c3d9933006a5e2f938429138c595c5fb28b91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-retrieve-the-net-framework-version-ccli"></a>Porady: pobieranie wersji programu .NET Framework (C++/CLI)
Poniższy przykład kodu pokazuje, jak można ustalić wersji aktualnie zainstalowany .NET Framework za pomocą <xref:System.Environment.Version%2A> właściwość, która jest wskaźnik do <xref:System.Version> obiekt, który zawiera informacje o wersji.  
  
## <a name="example"></a>Przykład  
  
```  
// dotnet_ver.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   Version^ version = Environment::Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write(".NET Framework version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
            build, major, minor, revision);  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)