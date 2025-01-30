<script lang="ts">
    import * as Card from "$lib/components/ui/card";
    import * as Form from "$lib/components/ui/form";
    import { Button } from "$lib/components/ui/button";
    import { Input } from "$lib/components/ui/input";
    import { Label } from "$lib/components/ui/label";
    import { goto } from "$app/navigation";

    let email = "";
    let password = "";

    async function handleSubmit() {
        // TODO: Implement login logic
        console.log("Login attempt:", { email, password });
    }
</script>

<div class="min-h-screen flex items-center justify-center bg-pink-50">
    <Card.Root class="w-[400px]">
        <Card.Header>
            <Card.Title class="text-2xl font-bold text-center">Welcome back</Card.Title>
            <Card.Description class="text-center">
                Login to your Ruthful Hearts account
            </Card.Description>
        </Card.Header>
        <Card.Content>
            <form on:submit|preventDefault={handleSubmit} class="space-y-4">
                <div class="space-y-2">
                    <Label for="email">Email</Label>
                    <Input 
                        id="email"
                        type="email" 
                        placeholder="Enter your email"
                        bind:value={email}
                        required
                    />
                </div>
                
                <div class="space-y-2">
                    <Label for="password">Password</Label>
                    <Input 
                        id="password"
                        type="password" 
                        placeholder="Enter your password"
                        bind:value={password}
                        required
                    />
                </div>

                <div class="flex justify-end">
                    <button 
                        type="button" 
                        class="text-sm text-pink-600 hover:underline"
                        on:click={() => goto('/auth/forgot-password')}
                    >
                        Forgot password?
                    </button>
                </div>

                <Button type="submit" class="w-full bg-pink-600 hover:bg-pink-700">
                    Sign in
                </Button>

                <div class="text-center text-sm">
                    Don't have an account?
                    <button 
                        type="button"
                        class="text-pink-600 hover:underline ml-1"
                        on:click={() => goto('/auth/register')}
                    >
                        Sign up
                    </button>
                </div>
            </form>
        </Card.Content>
    </Card.Root>
</div>
