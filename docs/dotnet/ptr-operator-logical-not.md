---
title: ptr::operator! | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ptr::operator!
- msclr::com::ptr::operator!
- ptr.operator!
- msclr.com.ptr.operator!
dev_langs: C++
helpviewer_keywords: ptr::operator!
ms.assetid: 7f4101dc-2045-42e7-abb1-6a30e17147f2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 82ff71586b495e42f7165f3782f41891767d583e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ptroperator"></a>ptr::operator!
Operatora, aby określić, czy należących do obiektu COM jest nieprawidłowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
bool operator!();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli należących do obiektu COM jest nieprawidłowy. `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Należących do obiektu COM jest prawidłowa, jeśli nie jest `nullptr`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie implementuje klasy CLR, która używa `com::ptr` opakowywać jego prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  `CreateInstance` Korzysta z funkcji członkowskiej `operator!` Aby ustalić, czy obiekt dokument ma już właściciela i tworzy nowe wystąpienie tylko, jeśli obiekt jest nieprawidłowy.  
  
```  
// comptr_op_not.cpp  
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
         if (m_ptrDoc) {  
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
 **Plik nagłówka** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Zobacz też  
 [elementy członkowskie PTR](../dotnet/ptr-members.md)   
 [PTR::operator — wartość logiczna](../dotnet/ptr-operator-bool.md)