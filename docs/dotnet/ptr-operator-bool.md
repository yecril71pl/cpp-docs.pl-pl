---
title: PTR::operator, wartość logiczna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr::operator bool
- ptr.operator bool
- operator bool
- msclr::com::ptr::operator bool
- msclr.com.ptr.operator bool
dev_langs:
- C++
helpviewer_keywords:
- ptr::operator bool
ms.assetid: 31123377-6ecd-4cef-9b75-3db3996fbcd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dcccfd23151d2e09f1fcafeb255dd7261ae2c12a
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163793"
---
# <a name="ptroperator-bool"></a>ptr::operator — wartość logiczna

Operator przy użyciu `com::ptr` w wyrażeniu warunkowym.

## <a name="syntax"></a>Składnia

```
operator bool();
```

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli należących do obiektu COM są prawidłowe; **false** inaczej.

## <a name="remarks"></a>Uwagi

Należących do obiektu COM jest prawidłowa, jeśli nie jest `nullptr`.

Ten operator faktycznie konwertuje `_detail_class::_safe_bool` co jest bezpieczniejszy niż `bool` , ponieważ nie można przekonwertować na typ całkowitoliczbowy.

## <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. `CreateInstance` Funkcja członkowska używa `operator bool` po utworzeniu nowego obiektu dokumentu, aby ustalić, czy jest prawidłowy i zapisuje do konsoli, jeśli jest.

```
// comptr_op_bool.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) { // uses operator bool
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Zobacz też

[ptr, składowe](../dotnet/ptr-members.md)<br/>
[ptr::operator!](../dotnet/ptr-operator-logical-not.md)