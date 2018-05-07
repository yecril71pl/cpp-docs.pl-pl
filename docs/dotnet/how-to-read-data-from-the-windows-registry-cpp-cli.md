---
title: 'Porady: odczytywanie danych z rejestru systemu Windows (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, reading from Windows Registry
- registry, reading
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87c882bcf2a7900e1f95ea968407c159333c6cb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-data-from-the-windows-registry-ccli"></a>Porady: odczytywanie danych z rejestru systemu Windows (C++/CLI)
Poniższy przykład kodu wykorzystuje <xref:Microsoft.Win32.Registry.CurrentUser> klucza można odczytać danych z rejestru systemu Windows. Najpierw podkluczy są wyliczane przy użyciu <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> metody, a następnie podklucz tożsamości jest otwarty przy użyciu <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody. Podobnie jak kluczy głównych każdy jest reprezentowany przez <xref:Microsoft.Win32.RegistryKey> klasy. Ponadto nowe <xref:Microsoft.Win32.RegistryKey> obiekt jest używany do wyliczenia pary klucz wartość.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 <xref:Microsoft.Win32.Registry> Klasy jest tylko kontener dla wystąpień statycznych <xref:Microsoft.Win32.RegistryKey>. Każde wystąpienie reprezentuje węzła głównego rejestru. Wystąpienia są <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, i <xref:Microsoft.Win32.Registry.Users>.  
  
 Ponadto aby jest statyczny, obiektów w <xref:Microsoft.Win32.Registry> klasy są tylko do odczytu. Ponadto wystąpień z <xref:Microsoft.Win32.RegistryKey> klasy, która tworzy się, aby uzyskać dostęp do zawartości rejestru obiektów, również są tylko do odczytu. Na przykład sposób zmienić to zachowanie, zobacz [porady: zapisu danych do rejestru systemu Windows (C + +/ CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).  
  
 Istnieją dwa dodatkowe obiekty w <xref:Microsoft.Win32.Registry> klasy: <xref:Microsoft.Win32.Registry.DynData> i <xref:Microsoft.Win32.Registry.PerformanceData>. Zarówno są wystąpieniami klasy <xref:Microsoft.Win32.RegistryKey> klasy. <xref:Microsoft.Win32.Registry.DynData> Zawiera informacje rejestru dynamicznych, która jest obsługiwana tylko w systemie Windows 98 i systemu Windows. <xref:Microsoft.Win32.Registry.PerformanceData> Obiekt może służyć do dostępu do informacji licznika wydajności dla aplikacji, które używają systemu monitorowania wydajności systemu Windows. <xref:Microsoft.Win32.Registry.PerformanceData> Informacje, które faktycznie nie są przechowywane w rejestrze i w związku z tym nie można wyświetlić przy użyciu Regedit.exe reprezentuje węzeł.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wpisywanie danych do rejestru systemu Windows (C + +/ CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)