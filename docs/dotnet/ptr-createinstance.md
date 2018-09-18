---
title: PTR::CreateInstance | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.CreateInstance
- msclr::com::ptr::CreateInstance
- msclr.com.ptr.CreateInstance
- ptr::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- ptr::CreateInstance
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f03a4f0cfb2b231e9a453009155308f7bf407db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112216"
---
# <a name="ptrcreateinstance"></a>ptr::CreateInstance
Tworzy wystąpienie obiektu COM w ramach `com::ptr`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   System::String ^ progid  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   const wchar_t * progid  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   REFCLSID rclsid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
*progid*<br/>
A `ProgID` ciągu.  
  
*pouter*<br/>
Wskaźnik interfejsu IUnknown obiektu agregacji (kontrolowanie IUnknown). Jeśli `pouter` nie zostanie określony, `NULL` jest używany.  
  
*cls_context*<br/>
Kontekst, w którym będzie uruchamiany kod, który zarządza nowo utworzony obiekt. Wartości te są pobierane z `CLSCTX` wyliczenia. Jeśli `cls_context` nie zostanie określony, wartość CLSCTX_ALL jest używany.  
  
*rclsid*<br/>
`CLSID` skojarzony z danymi i kod, który będzie używany do utworzenia obiektu.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `com::ptr` już posiada odwołanie do obiektu COM `CreateInstance` zgłasza <xref:System.InvalidOperationException>.  
  
 Ta funkcja wywołuje `CoCreateInstance` i używa <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> do konwersji wszelkie błędy `HRESULT` na odpowiedni wyjątek.  
  
## <a name="remarks"></a>Uwagi  
 `CreateInstance` używa `CoCreateInstance` do utworzenia nowego wystąpienia określonego obiektu, identyfikowany albo z identyfikator ProgID i CLSID. `com::ptr` Odwołuje się do nowo utworzonego obiektu i automatycznie zwolni wszystkich należących do odwołania na zniszczenia.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. Konstruktory klasy użycie dwóch różnych metod `CreateInstance` można utworzyć obiektu dokumentu, z identyfikator ProgID albo z CLSID oraz CLSCTX.  
  
```  
// comptr_createinstance.cpp  
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
   XmlDocument(REFCLSID clsid, DWORD clsctx) {  
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      // create the class from a progid string  
      XmlDocument doc1("Msxml2.DOMDocument.3.0");  
  
      // or from a clsid with specific CLSCTX  
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówkowy** \<msclr\com\ptr.h >  
  
 **Namespace** msclr::com  
  
## <a name="see-also"></a>Zobacz też  
 [ptr, składowe](../dotnet/ptr-members.md)