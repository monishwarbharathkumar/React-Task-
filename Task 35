import { useState } from "react";
import {
  ThemeProvider,
  createTheme,
  Box,
  Card,
  CardHeader,
  CardContent,
  CardActions,
  TextField,
  Button,
  Typography,
  Container
} from "@mui/material";

const theme = createTheme({
  palette: {
    primary: { main: "#1976d2" },
    secondary: { main: "#9c27b0" }
  }
});

export default function App() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  const handleSubmit = e => {
    e.preventDefault();
    alert(`Welcome ${email}`);
  };

  return (
    <ThemeProvider theme={theme}>
      <Container maxWidth="sm" sx={{ py: 6 }}>
        <Typography variant="h4" textAlign="center" mb={4}>
          MUI Demo
        </Typography>

        <Card sx={{ mb: 4, p: 1 }}>
          <CardHeader
            title="Premium Headphones"
            subheader="$129.99"
          />
          <CardContent>
            <Typography color="text.secondary">
              Wireless headphones with noise cancellation and
              high-quality sound.
            </Typography>
          </CardContent>
          <CardActions sx={{ px: 2, pb: 2 }}>
            <Button variant="contained" color="primary">
              Buy Now
            </Button>
            <Button variant="outlined" color="secondary">
              Details
            </Button>
          </CardActions>
        </Card>

        <Card sx={{ p: 3 }}>
          <Typography variant="h5" mb={3}>
            Login
          </Typography>

          <Box
            component="form"
            onSubmit={handleSubmit}
            sx={{ display: "flex", flexDirection: "column", gap: 2 }}
          >
            <TextField
              label="Email"
              type="email"
              value={email}
              onChange={e => setEmail(e.target.value)}
              fullWidth
              required
            />

            <TextField
              label="Password"
              type="password"
              value={password}
              onChange={e => setPassword(e.target.value)}
              fullWidth
              required
            />

            <Button
              type="submit"
              variant="contained"
              size="large"
              sx={{ mt: 1 }}
            >
              Login
            </Button>
          </Box>
        </Card>
      </Container>
    </ThemeProvider>
  );
}
