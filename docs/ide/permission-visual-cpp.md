---
title: '&lt;uprawnienie&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: ecf027600b23a640d1dc0cd68b75ffa5eb1b3659
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744612"
---
# <a name="ltpermissiongt-visual-c"></a>&lt;uprawnienie&gt; (Visual C++)

\<Uprawnienia > znacznik umożliwia dokumentowanie dostępu do elementu członkowskiego. <xref:System.Security.PermissionSet> Umożliwia określenie dostęp do elementu członkowskiego.

## <a name="syntax"></a>Składnia

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Parametry

*Element członkowski*<br/>
Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i wykonuje translację `member` nazwę kanoniczną element w danych wyjściowych XML.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.

Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../ide/see-visual-cpp.md).

*description*<br/>
Opis dostępu do elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

Kompilator języka Visual C++ będzie próbował rozpoznać odwołania cref w jednym przebiegu za pomocą komentarzy dokumentacji.  W związku z tym, jeśli przy użyciu reguł wyszukiwania C++, symbolu nie można odnaleźć kompilatora odwołania zostaną oznaczone jako nierozwiązane. Zobacz [ \<SeeAlso — >](../ide/seealso-visual-cpp.md) Aby uzyskać więcej informacji.

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

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)
