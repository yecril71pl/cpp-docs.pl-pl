---
title: 'Porady: wpisywanie danych do rejestru systemu Windows (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8bb95ab9a70fd0144256f85d3fae6ccc3c034c1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-write-data-to-the-windows-registry-ccli"></a>Porady: wpisywanie danych do rejestru systemu Windows (C++/CLI)
Poniższy przykład kodu wykorzystuje <xref:Microsoft.Win32.Registry.CurrentUser> klawisz, aby utworzyć wystąpienie zapisywalny <xref:Microsoft.Win32.RegistryKey> klasy odpowiadający **oprogramowania** klucza. <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> Metody jest następnie używany do tworzenia klucza, a następnie dodaj do par klucz/wartość.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 .NET Framework umożliwia uzyskiwanie dostępu do rejestru z <xref:Microsoft.Win32.Registry> i [RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx) klasy, które są zdefiniowane w <xref:Microsoft.Win32> przestrzeni nazw. **Rejestru** klasy to kontener dla wystąpień statycznych <xref:Microsoft.Win32.RegistryKey> klasy. Każde wystąpienie reprezentuje węzła głównego rejestru. Wystąpienia są <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, i <xref:Microsoft.Win32.Registry.Users>.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: odczytywanie danych z rejestru systemu Windows (C + +/ CLI)](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)