---
title: '> uprawnień &lt;(C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: e7f0a59c85e3fa28d24e44953e207151c3afa0f4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988680"
---
# <a name="ltpermissiongt"></a>&gt; uprawnień &lt;

Tag > uprawnień \<umożliwia dokumentowanie dostępu do elementu członkowskiego. <xref:System.Security.PermissionSet> pozwala określić dostęp do elementu członkowskiego.

## <a name="syntax"></a>Składnia

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Parametry

*członkiem*<br/>
Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.  Ujmij nazwę w pojedyncze lub podwójne cudzysłowy.

Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [\<see >](see-visual-cpp.md).

*zharmonizowan*<br/>
Opis dostępu do elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

Kompilator MSVC podejmie próbę rozpoznania odwołań cref w jednym przejściu poprzez Komentarze do dokumentacji.  W związku z tym, C++ w przypadku używania reguł odnośników nie znaleziono symbolu przez kompilator, odwołanie zostanie oznaczone jako nierozwiązane. Aby uzyskać więcej informacji, zobacz [\<seealso — >](seealso-visual-cpp.md) .

## <a name="example"></a>Przykład

```cpp
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

[Dokumentacja XML](xml-documentation-visual-cpp.md)
