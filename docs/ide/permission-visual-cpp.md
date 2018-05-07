---
title: '&lt;uprawnienie&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- permission
- <permission>
dev_langs:
- C++
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e13824780a5c73d4423bd544a97108b45d1b770a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltpermissiongt-visual-c"></a>&lt;uprawnienie&gt; (Visual C++)
\<Uprawnienia > znacznik umożliwia dostęp do elementu członkowskiego dokumentu. <xref:System.Security.PermissionSet> Umożliwia określenie dostępu do elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy element podanego kodu istnieje i wykonuje translację `member` nazwę kanoniczną element wyjściowy element XML.  Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  
  
 Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.  
  
 Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../ide/see-visual-cpp.md).  
  
 `description`  
 Opis dostępu do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
 Kompilator Visual C++ podejmie próbę rozpoznawania odwołań cref w jednym przebiegu za pośrednictwem komentarzy do dokumentacji.  W związku z tym jeśli przy użyciu reguł wyszukiwania C++, symbol nie znaleziono przez kompilator, odwołanie zostanie oznaczona jako nierozwiązane. Zobacz [ \<seealso >](../ide/seealso-visual-cpp.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
  
```  
// xml_permission_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_permission_tag.dll  
using namespace System;  
/// Text for class TestClass.  
public ref class TestClass {  
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>  
   void Test() {}  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)