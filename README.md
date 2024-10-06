# senthilnathan.js.org

// Convert response headers to lowercase to ensure access and log the headers to console
  const headers = Object.keys(response.headers).reduce((acc, key) => {
    acc[key.toLowerCase()] = response.headers[key];
    return acc;
  }, {} as Record<string, string>);

  // Print the converted headers to the console
  console.log('Converted Response Headers:', headers);
