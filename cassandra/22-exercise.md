# Blogging application

**Features**:
- Create a blogging account
- Publish posts
- Tag the posts, and posts can be searched using those tags
- Access patterns:
    - Retrieve all posts from a blog
    - Retrieve the blog posts paginate by two
    - Retrieve all posts with a specific tag 
---

**Create keyspace**
```
CREATE KEYSPACE weblog WITH REPLICATION = {'class':'SimpleStrategy', 'replication_factor': 1};

USE weblog;
```

**blog metadata and user info**
```
CREATE TABLE blogs (
    id uuid PRIMARY KEY, 
    blog_name text,
    author text, 
    email text, 
    password varchar);

INSERT INTO blogs (id, blog_name, author, email, password)
    VALUES ( uuid(), 'My Tech Blog', 'Lucian Neghina', 'lucian@esolutions.ro', 'someHashed#passwrd');

```

**individual posts**
```
CREATE TABLE posts (
    id timeuuid, 
    blog_id uuid, 
    posted_on timestamp, 
    title text, 
    content text, 
    tags set<varchar>, 
    PRIMARY KEY(blog_id, id)
);

// first my post 
INSERT INTO posts (id, blog_id, title, content, tags, posted_on) 
    VALUES (now(), 3014afab-efa9-455e-8f5c-ca3597f657e8, 'First post', 'nosql demo blog', {'nosql','cassandra'}, toTimeStamp(now()));

// second post
INSERT INTO posts (id, blog_id, title, content, tags, posted_on) 
    VALUES (now(), 3014afab-efa9-455e-8f5c-ca3597f657e8, 'Processing', 'distributed processing framework', {'bigdata','spark'}, toTimeStamp(now()));

SELECT * FROM posts;

```

---

Q1: Retrieve my posts paginate by two
```
// first page
SELECT * FROM posts WHERE blog_id = 3014afab-efa9-455e-8f5c-ca3597f657e8 ORDER BY id DESC LIMIT 2;

// next page 
SELECT * FROM posts WHERE blog_id = 3014afab-efa9-455e-8f5c-ca3597f657e8 AND id < 12c97ec0-5c44-11ed-9aec-9b89c16b65a4 ORDER BY id DESC LIMIT 2;
```