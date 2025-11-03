# Q Unit Testing (xUnit & Moq)
## Q. How do you mock dependencies using Moq in xUnit?

var mockRepo = new Mock<IUserRepository>();
mockRepo.Setup(r => r.GetUser(1)).ReturnsAsync(new User { Id = 1, Name = "John" });
```
var service = new UserService(mockRepo.Object);
var result = await service.GetUser(1);

Assert.Equal("John", result.Name);
```
## Q. What’s the Arrange-Act-Assert (AAA) pattern in testing?
Arrange: Setup test objects and mocks.

Act: Execute the method under test.

Assert: Verify expected results.

## Q. How do you test asynchronous methods in xUnit?
Mark the test with async Task and use await:
```
[Fact]
public async Task GetUser_ShouldReturnUser()
{
    var result = await _service.GetUser(1);
    Assert.NotNull(result);
}
```
