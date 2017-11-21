---
title: PTR::PTR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ptr::ptr
- ptr.ptr
- msclr.com.ptr.ptr
- msclr::com::ptr::ptr
dev_langs: C++
helpviewer_keywords: ptr::ptr
ms.assetid: 4f5883b4-7c0a-46c6-aa9f-4e49eed463eb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99016a9006bb13be70fe38fd222ad25a08792b20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ptrptr"></a>ptr::ptr
Konstruuje `com::ptr` opakowywać obiektu COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
ptr();  
ptr(  
   _interface_type * p  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `P`  
 Wskaźnika interfejsu COM.  
  
## <a name="remarks"></a>Uwagi  
 Przypisuje konstruktora bez argumentów `nullptr` do uchwytu obiektu źródłowego. Kolejne wywołania `com::ptr` będzie zweryfikować wewnętrznego obiektu i dyskretnej niepowodzeniem, dopóki faktycznie utworzony lub dołączyć obiektu.  
  
 Konstruktor one-argument — dodaje odwołanie do obiektu modelu COM, ale nie zwalnia odwołanie do obiektu wywołującego, dlatego należy wywołać element wywołujący `Release` obiektu modelu COM, aby rzeczywiście formantu. Gdy `com::ptr`na destruktora jest wywoływana automatycznie opublikuje jego odwołania do obiektu COM.  
  
 Przekazywanie `NULL` do tego konstruktora jest taka sama jak wywołanie wersji bez argumentów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie implementuje klasy CLR, która używa `com::ptr` opakowywać jego prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. Jednak przedstawia użycie obie wersje konstruktora.  
  
```  
// comptr_ptr.cpp  
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
   // construct the internal com::ptr with a null interface  
   // and use CreateInstance to fill it  
   XmlDocument(String^ progid) {  
      m_ptrDoc.CreateInstance(progid);     
   }  
  
   // construct the internal com::ptr with a COM object  
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
  
   try {  
      // create an XML DOM document object  
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,   
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));  
      // construct the ref class with the COM object  
      XmlDocument doc1(pDoc);  
  
      // or create the class from a progid string  
      XmlDocument doc2("Msxml2.DOMDocument.3.0");  
   }  
   // doc1 and doc2 destructors are called when they go out of scope  
   // and the internal com::ptr releases its reference to the COM object  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
   finally {  
      if (NULL != pDoc) {  
         pDoc->Release();        
      }  
   }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Zobacz też  
 [elementy członkowskie PTR](../dotnet/ptr-members.md)   
 [PTR::CreateInstance](../dotnet/ptr-createinstance.md)   
 [PTR:: ~ ptr](../dotnet/ptr-tilde-ptr.md)