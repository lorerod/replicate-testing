# PouchDB Replication Test Harness

A simple HTML-based tool for testing PouchDB replication with large attachments across different devices and memory constraints.

## Instructions to Run Locally

### 1. Run CouchDB locally

```bash
docker run -d --name couch \
  -e COUCHDB_USER=admin \
  -e COUCHDB_PASSWORD=pass \
  -p 5984:5984 \
  -v couch-data:/opt/couchdb/data \
  couchdb:3
```

### 2. Access Fauxton UI

Open your browser and go to: http://localhost:5984/_utils/
- **Username**: admin
- **Password**: pass

### 3. Create a database

In Fauxton, create a new database (e.g., `media`).

### 4. Upload documents with attachments

In Fauxton:
1. Create new documents
2. Use the **Attachments** tab to add images/videos
3. Upload your test files with various sizes

### 5. Serve replicate.html

Save the replication test code into a file named `replicate.html`. Then run a quick web server:

**Option 1: Python**
```bash
python3 -m http.server 8080
```

**Option 2: Node.js**
```bash
npx http-server -p 8080
```

### 6. Open the test interface

Open your browser and go to: http://localhost:8080/replicate.html

### 7. Test replication

1. Enter **Couch URL**: `http://admin:pass@localhost:5984`
2. Enter **DB Name**: `media`
3. Adjust batch settings as needed:
   - `batch_size`: Number of documents per batch 
   - `batches_limit`: Maximum number of batches to process
4. Click **Start pull**
5. Use the dropdown to pick a document and preview its attachments
