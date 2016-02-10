#include "stdafx.h"
#include "rotate.h"

#include "rotateDoc.h"
#include "rotateView.h"

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
#define WM_MYMESSAGE WM_USER+1

/////////////////////////////////////////////////////////////////////////////
// CRotateView

IMPLEMENT_DYNCREATE(CRotateView, CView)

BEGIN_MESSAGE_MAP(CRotateView, CView)
	//{{AFX_MSG_MAP(CRotateView)
	ON_WM_CREATE()
	ON_WM_TIMER()
	ON_WM_DESTROY()
	//}}AFX_MSG_MAP
	 
	// Standard printing commands
    ON_COMMAND(ID_FILE_PRINT, CView::OnFilePrint)
	ON_COMMAND(ID_FILE_PRINT_DIRECT, CView::OnFilePrint)
	ON_COMMAND(ID_FILE_PRINT_PREVIEW, CView::OnFilePrintPreview)
	ON_MESSAGE(WM_MYMESSAGE,OnMyMessage)
END_MESSAGE_MAP()

/////////////////////////////////////////////////////////////////////////////
// CRotateView construction/destruction

CRotateView::CRotateView()
{
m_dEscapement=0;	// TODO: add construction code here

}

CRotateView::~CRotateView()
{
}

BOOL CRotateView::PreCreateWindow(CREATESTRUCT& cs)
{
	// TODO: Modify the Window class or styles here by modifying
	//  the CREATESTRUCT cs

	return CView::PreCreateWindow(cs);
}

/////////////////////////////////////////////////////////////////////////////
// CRotateView drawing

void CRotateView::OnDraw(CDC* pDC)
{
	CRotateDoc* pDoc = GetDocument();
	ASSERT_VALID(pDoc);
	// TODO: add draw code for native data here
}

/////////////////////////////////////////////////////////////////////////////
// CRotateView printing

BOOL CRotateView::OnPreparePrinting(CPrintInfo* pInfo)
{
	// default preparation
	return DoPreparePrinting(pInfo);
}

void CRotateView::OnBeginPrinting(CDC* /*pDC*/, CPrintInfo* /*pInfo*/)
{
	// TODO: add extra initialization before printing
}

void CRotateView::OnEndPrinting(CDC* /*pDC*/, CPrintInfo* /*pInfo*/)
{
	// TODO: add cleanup after printing
}

/////////////////////////////////////////////////////////////////////////////
// CRotateView diagnostics

#ifdef _DEBUG
void CRotateView::AssertValid() const
{
	CView::AssertValid();
}

void CRotateView::Dump(CDumpContext& dc) const
{
	CView::Dump(dc);
}

CRotateDoc* CRotateView::GetDocument() // non-debug version is inline
{
	ASSERT(m_pDocument->IsKindOf(RUNTIME_CLASS(CRotateDoc)));
	return (CRotateDoc*)m_pDocument;
}
#endif //_DEBUG

/////////////////////////////////////////////////////////////////////////////
// CRotateView message handlers

int CRotateView::OnCreate(LPCREATESTRUCT lpCreateStruct) 
{
	if (CView::OnCreate(lpCreateStruct) == -1)
		return -1;
	
	// TODO: Add your specialized creation code here
	SetTimer(1,200,NULL);
	
	return 0;
}
LRESULT CRotateView::OnMyMessage(WPARAM wParam,LPARAM lParam)
{
	CClientDC dc(this);
	m_dEscapement=(m_dEscapement+100)%3600;
	CFont fontRotate;
	fontRotate.CreateFont(30,0,m_dEscapement,0,0,0,0,0,0,0,0,0,0,0);
	CFont*pOldFont=dc.SelectObject(&fontRotate);
	CRect rClient;
    GetClientRect(rClient);
	dc.FillSolidRect(&rClient,RGB(255,255,255));
	dc.TextOut(rClient.right/2,rClient.bottom/2,"^(*￣(oo)￣)^我想你了");
    dc.SelectObject(pOldFont);
	return 0;

}
void CRotateView::OnTimer(UINT nIDEvent) 
{
	SendMessage(WM_MYMESSAGE);
	// TODO: Add your message handler code here and/or call default
	
	CView::OnTimer(nIDEvent);
}



void CRotateView::OnDestroy() 
{
	CView::OnDestroy();
	KillTimer(1);
	// TODO: Add your message handler code here
	
}
