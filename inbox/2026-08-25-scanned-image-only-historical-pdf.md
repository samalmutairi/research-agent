# Finding: scanned image-only historical document PDF for extraction

- Date: 2026-08-25
- Asked by: Agent X / this workspace
- Method: hub cache (miss), then playbook (4 WebSearch, 1 HTML WebFetch, 1 PDF download)

## Question

Find a scanned, image-only historical document PDF (no embedded text layer, e.g. a declassified document) and hand it to the Document Extractor to answer a content question (e.g. what the document says on its first page).

## Answer

Downloaded a declassified National Security Council memorandum to Dr. Kissinger, dated 8 September 1971 (from Arnold Nachmanoff, re: a committee meeting of September 9, 1971), hosted by the National Security Archive at George Washington University. The National Security Archive serves its declassified documents as raw scan PDFs and publishes OCR text as a separate web page ("View OCR of the document"), which indicates the PDFs themselves are image-only scans of typewritten originals. The file is a valid 3-page PDF (154 KB). Contents were not opened or read; the content question (what the document says on its first page) is pending Document Extractor processing.

## Claims

- The National Security Archive hosts declassified primary-source PDFs and offers OCR as a separate page, implying image-only scan PDFs — https://nsarchive.gwu.edu/document/24604-document-25-nsc-memo-rostow-lbj-death-che-guevara-october-11-1967-declassified
- Direct scan PDF: NSC memorandum to Kissinger, 8 September 1971, declassified under E.O. 12958 (9/14/2000) — https://nsarchive.gwu.edu/sites/default/files/documents/3677702/04-National-Security-Council-Memorandum-to.pdf

## Hits

- MEMORANDUM (NSC, 8 Sep 1971, to Dr. Kissinger) — https://nsarchive.gwu.edu/sites/default/files/documents/3677702/04-National-Security-Council-Memorandum-to.pdf
- Memorandum of Conversation, Brzezinski, 1980 (alternate scan) — https://nsarchive.gwu.edu/sites/default/files/documents/3696543/Document-16-Memorandum-of-Conversation-National.pdf
- NSC Memo, Rostow-LBJ, "Death of 'Che' Guevara," Oct 11 1967 (doc page; PDF link not exposed in rendered HTML) — https://nsarchive.gwu.edu/document/24604-document-25-nsc-memo-rostow-lbj-death-che-guevara-october-11-1967-declassified
- Virtual Reading Room | National Security Archive — https://nsarchive.gwu.edu/virtual-reading-room
- JACOBO ARBENZ — OPERATIONS AGAINST, CIA FOIA reading room (download blocked by redirect loop) — https://www.cia.gov/readingroom/docs/DOC_0000919960.pdf
- Special History of the Pueblo Incident 1968 (governmentattic; site notes OCR-enabled PDFs, so skipped) — https://www.governmentattic.org/13docs/SpecHistPUEBLOincident_1968.pdf

## Files

- /Users/samalmutairi/ws/Research agent/inbox/files/nsc-memo-kissinger-1971/04-National-Security-Council-Memorandum-to.pdf — for the Document Extractor (contents not read)

## Lane

- web (historical archives / declassified documents)

## Gaps

- The absence of an embedded text layer was inferred from the National Security Archive's practice of publishing OCR separately, not verified by inspecting the PDF (contents intentionally not opened).
- The content question ("what does the document say on its first page?") is pending extraction by the Document Extractor.
- CIA FOIA reading room direct download failed (curl redirect loop, likely bot protection); not retried.
