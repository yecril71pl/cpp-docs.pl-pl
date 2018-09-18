---
title: PTR::PTR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr::ptr
- ptr.ptr
- msclr.com.ptr.ptr
- msclr::com::ptr::ptr
dev_langs:
- C++
helpviewer_keywords:
- ptr::ptr
ms.assetid: 4f5883b4-7c0a-46c6-aa9f-4e49eed463eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4f4df3e8059a56b137b2a4750177af1269cb6a5c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107029"
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
*P*<br/>
Wskaźnik interfejsu COM.  
  
## <a name="remarks"></a>Uwagi  
 Przypisuje konstruktora bez argumentów `nullptr` do podstawowego dojścia obiektu. Kolejne wywołania `com::ptr` będzie zweryfikować obiekt wewnętrzny i dyskretnie się niepowodzeniem, dopóki obiekt jest faktycznie utworzone lub dołączone.  
  
 Konstruktor one-argument — dodaje odwołanie do obiektu COM, ale nie spowoduje zwolnienia odwołanie do obiektu wywołującego, dzięki czemu obiekt wywołujący musi wywoływać `Release` obiektu COM naprawdę oddawać kontroli. Gdy `com::ptr`jego destruktor jest wywoływany automatycznie zwolni jego odwołania do obiektu COM.  
  
 Przekazywanie `NULL` do tego konstruktora jest taka sama jak wersja bez argumentów podczas wywoływania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. Pokazuje użycie obie wersje konstruktora.  
  
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
 **Plik nagłówkowy** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Zobacz też  
 [elementy członkowskie PTR](../dotnet/ptr-members.md)   
 [PTR::CreateInstance](../dotnet/ptr-createinstance.md)   
 [ptr::~ptr](../dotnet/ptr-tilde-ptr.md)