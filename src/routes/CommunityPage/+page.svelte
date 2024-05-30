<script>
  // Array to store community posts
  let posts = [
    {
      id: 1,
      author: "John Doe",
      content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
      comments: [
        { id: 1, author: "Jane Smith", content: "Great post!" },
        { id: 2, author: "Mike Johnson", content: "I agree!" }
      ]
    },
    {
      id: 2,
      author: "Alice Johnson",
      content: "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      comments: []
    }
  ];

  // Function to add a new post
  function addPost() {
    const newPost = {
      id: posts.length + 1,
      author: "New User",
      content: "New post content",
      comments: []
    };
    posts = [newPost, ...posts];
  }

  // Function to add a new comment to a post
  function addComment(postId, commentContent) {
    const postIndex = posts.findIndex(post => post.id === postId);
    if (postIndex !== -1) {
      posts[postIndex].comments.push({
        id: posts[postIndex].comments.length + 1,
        author: "New Commenter",
        content: commentContent
      });
    }
  }
</script>

<main class="bg-gray-100 min-h-screen">
  <div class="container mx-auto px-4 py-8">
    <h1 class="text-3xl lg:text-4xl font-bold text-gray-800 mb-8 text-center">Community</h1>
    <!-- New Post Form -->
    <form on:submit|preventDefault={addPost} class="mb-6">
      <textarea rows="4" placeholder="Write your post here..." class="w-full px-4 py-2 mb-2 border border-gray-300 rounded-md focus:outline-none focus:border-blue-500"></textarea>
      <button type="submit" class="px-4 py-2 bg-blue-500 text-white font-semibold rounded-md shadow-md hover:bg-blue-600 hover:text-white transition-colors">Post</button>
    </form>
    <!-- Display Posts -->
    {#each posts as post}
      <div class="bg-white rounded-lg shadow-md p-4 mb-4">
        <p class="text-gray-700 font-semibold">Posted by {post.author}</p>
        <p class="text-gray-800">{post.content}</p>
        <!-- Comments Section -->
        <div class="mt-4">
          {#if post.comments.length > 0}
            <h3 class="text-lg font-semibold mb-2">Comments:</h3>
            {#each post.comments as comment}
              <div class="bg-gray-100 rounded-md p-2 mb-2">
                <p class="text-gray-700 font-semibold">{comment.author}:</p>
                <p class="text-gray-800">{comment.content}</p>
              </div>
            {/each}
          {/if}
          <!-- New Comment Form -->
          <form on:submit|preventDefault={() => addComment(post.id, post.newComment)} class="mt-4">
            <textarea rows="2" bind:value={post.newComment} placeholder="Write a comment..." class="w-full px-4 py-2 mb-2 border border-gray-300 rounded-md focus:outline-none focus:border-blue-500"></textarea>
            <button type="submit" class="px-4 py-2 bg-blue-500 text-white font-semibold rounded-md shadow-md hover:bg-blue-600 hover:text-white transition-colors">Comment</button>
          </form>
        </div>
      </div>
    {/each}
  </div>
</main>

<style>
  textarea {
    resize: none;
  }
</style>
